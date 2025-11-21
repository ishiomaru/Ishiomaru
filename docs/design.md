# 設計書（design.md）

> 本設計書は `docs/requirements.md` に基づき、GitHub special repository README の情報設計・技術設計を示す。

## 1. 全体像

| 視点         | 内容                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------- |
| 目的         | 採用担当・OSS コミュニティが 5 秒以内でスキル・実績を把握できるプロフィールを提供する       |
| デザイン原則 | schier.co のような洗練ミニマル & Google 製品級の直感 UX（余白・階層・タイポグラフィを重視） |
| 主技術       | Markdown, SVG, GitHub Actions (Node.js 18), Shields.io, readme-stats-services               |
| 更新方式     | 動的セクションは Action で 24h ごとに自動更新／静的セクションは手動コミット                 |
| KPI          | なし                                                                                        |

## 2. UI / 情報アーキテクチャ

```
┌──────── First View ───────────┐
│ Hero image / header           │  tighten copy + optional badge │
├───────────────────────────────┤
│ About                         │  short list of focus + goals  │
├───────────────────────────────┤
│ Tech / Skill badge table      │  icon + text for each tool     │
├───────────────────────────────┤
│ Stats badges (optional)       │  GitHub / streak images        │
├───────────────────────────────┤
│ Fun facts + Contact           │  concise bullet list + icons  │
└───────────────────────────────┘
```

### 2.1 デザイン原則

- **Simple & Focused**: `example.md` のように情報を絞り込み、About・Tech・Contact を並列に見せることで読みやすさを確保。
- **Icon-First Tech**: Devicon / Shields で各ツールにアイコンを添え、Markdown の表でも視線を集めやすくする。
- **Accessible Colors**: Light Tritanopia パレットに沿いつつ、GitHub 表示で変化しても意味が保てる高コントラストな文字とバッジ。
- **Minimal Motion**: GitHub では CSS アニメーションが無効なので、記述ではなくtyped copy でアテンションを引く。

### レイアウト指針

- **1 viewport focus**: About/Tech/Contact が一画面に見えることを確認し、長大な説明文や複雑なグリッドを避ける。
- **Stacked sections**: Markdown セクションを縦積みにし、`---` で区切って視線を誘導。画像は `max-width:100%` で扱う。
- **Icons & badges**: 単一行にまとめづらい場合テーブルを使い、アイコン+テキスト+ノートで構成する。

### 2.2 カラーパレット（Light Tritanopia）

| 変数          | HEX     | 用途                   |
| ------------- | ------- | ---------------------- |
| `--bg`        | #FFFFFF | 背景                   |
| `--fg`        | #202124 | 本文                   |
| `--accent`    | #007ACC | リンク・アイコンホバー |
| `--secondary` | #586069 | サブテキスト           |

WCAG AA コントラスト比 ≥ 4.5 を保持。

- Tech stack セクションは Devicon / Shields を使用し、skill icon + テキストで言語を示すことで GitHub 上でも直感的に伝わるようにする。

## 3. デザイントークン

| Token       | 値               | 用途                 |
| ----------- | ---------------- | -------------------- |
| `space-1`   | 4px              | 最小余白             |
| `space-2`   | 8px              | コンポーネント内余白 |
| `space-3`   | 16px             | セクション余白       |
| `space-4`   | 32px             | セクション間隔       |
| `font-base` | 1rem / 16px      | 本文                 |
| `font-lg`   | 1.5625rem / 25px | h2                   |
| `font-xl`   | 2.441rem / 39px  | h1                   |

これらを README 内の inline-style もしくは `<style>` ブロックで管理し、一貫性を担保。

## 4. コンポーネント設計

| コンポーネント | 機能                              | 実装                                |
| -------------- | --------------------------------- | ----------------------------------- |
| `Header`       | 氏名・肩書・アイコン              | Markdown 見出し + Shield Icon       |
| `BadgeList`    | 技術バッジ                        | Shields.io SVG をインライン埋め込み |
| `StatsPanel`   | `Stats`, `Streak`, `TopLang` 画像 | GitHub Readme Stats API 画像 URL    |
| `RepoCard`     | Featured Repo 要約                | `gh api` + SVG template 生成        |
| `SocialLinks`  | SNS アイコンリンク                | Simple Icons + href                 |

アニメーションは `opacity` と `transform` を用いた 0.2s フェードインのみ（`prefers-reduced-motion` 配慮）。

## 5. GitHub Actions ワークフロー

```yaml
name: Update README stats
on:
  schedule:
    - cron: "0 3 * * *" # 毎日 12:00 JST
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Generate stats images
        uses: anuraghazra/github-readme-stats@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          # 画像を /assets に保存
      - name: Commit & push
        run: |
          git config user.name  github-actions
          git config user.email github-actions@users.noreply.github.com
          git add ./assets/
          git commit -m "chore: update stats images [skip ci]" || echo "No change"
          git push
```

- **実行時間** < 30 秒。Image 生成だけでビルドレス。
- Rate-limit 対策: 失敗時 `actions/timeout` で 30m 再試行 3 回。

## 6. フォルダ構成

```
└─ <username>
   ├─ README.md
   ├─ assets/               # 生成画像
   ├─ .github/
   │  └─ workflows/
   │     └─ update-stats.yml
   └─ docs/
      ├─ requirements.md
      └─ design.md
```

## 7. パフォーマンス & アクセシビリティ

- 画像は `?cacheSeconds=86400` で CDN キャッシュ。
- LCP 画像は先頭に `<img loading="eager" width="100%">`。
- `aria-label` を各リンクに付与。
- Lighthouse モバイル Performance ≥ 90 を目標。

## 8. テスト計画

| 種類     | ツール        | 内容                             |
| -------- | ------------- | -------------------------------- |
| Lint     | markdownlint  | README 文法チェック              |
| ユニット | n/a           | シェルスクリプト Function テスト |
| E2E      | Lighthouse CI | LCP / a11y スコア測定            |
| Visual   | Shot-Scraper  | Diff で README 画像崩れ検知      |

## 9. 移行・拡張性

- なし

---

## GitHub Rendering Constraints

- GitHub README は一部の CSS/STYLE タグを削除するため、最終出力の確認を GitHub 上で必ず行い、docs にスクリーンショットや挙動を記録する。
- Fallback では Markdown のレイアウトを依存先とし、style block が無効でもテキストが読める構造を維持する。
- Skill icon は CDN 依存なので、表示されないことも想定し `alt` とテキストでツール名を補完する。

以上。設計変更があれば本書を更新する。
