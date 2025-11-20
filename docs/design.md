# 設計書（design.md）

> 本設計書は `docs/requirements.md` に基づき、GitHub special repository README の情報設計・技術設計を示す。特に **`schier.co` をベンチマークとしたミニマルかつ洗練された UI/UX** を最優先事項としている。

## 1. 全体像

| 視点     | 内容                                                                                  |
| -------- | ------------------------------------------------------------------------------------- |
| 目的     | 採用担当・OSS コミュニティが 5 秒以内でスキル・実績を把握できるプロフィールを提供する |
| 主技術   | Markdown, SVG, GitHub Actions (Node.js 18), Shields.io, readme-stats-services         |
| 更新方式 | 動的セクションは Action で 24h ごとに自動更新／静的セクションは手動コミット           |
| KPI      | なし                                                                                  |

## 2. UI / 情報アーキテクチャ

```
┌──────── First View ───────────┐
│ Header / Self-Intro           │  約 200〜250 字, アイコン(SVG) │
├───────────────────────────────┤
│ Tech Stacks / Skills          │  バッジ横並び, 折返し対応 │
├───────────────────────────────┤
│ GitHub Stats・Streak・TopLang │  3 枚横並び (≤768px で縦) │
├───────────────────────────────┤
│ Featured Repositories (3)     │  star / lang / desc Card │
├───────────────────────────────┤
│ Contact / Social Links        │  アイコン+テキスト │
└───────────────────────────────┘
```

### レイアウト指針（8pt グリッド）

- 全要素・余白を **8pt グリッド** にスナップ。`schier.co` の視認性・余白感を踏襲。
- **1 ブロック ≤ 350px** を目安に要素間マージンを調整し、縦 800px（ノート PC）で 1 スクロール以内に収める。
- モバイル（≤480px）は縦積みレイアウト、SVG/画像は `max-width:100%`。
- 各セクションに `id` を付与して内部リンクを許容。

### カラーパレット（Light Tritanopia）

| 変数          | HEX     | 用途                   |
| ------------- | ------- | ---------------------- |
| `--bg`        | #FFFFFF | 背景                   |
| `--fg`        | #202124 | 本文                   |
| `--accent`    | #007ACC | リンク・アイコンホバー |
| `--secondary` | #586069 | サブテキスト           |

WCAG AA コントラスト比 ≥ 4.5 を保持。

## 3. コンポーネント設計

| コンポーネント | 機能                              | 実装                                |
| -------------- | --------------------------------- | ----------------------------------- |
| `Header`       | 氏名・肩書・アイコン              | Markdown 見出し + Shield Icon       |
| `BadgeList`    | 技術バッジ                        | Shields.io SVG をインライン埋め込み |
| `StatsPanel`   | `Stats`, `Streak`, `TopLang` 画像 | GitHub Readme Stats API 画像 URL    |
| `RepoCard`     | Featured Repo 要約                | `gh api` + SVG template 生成        |
| `SocialLinks`  | SNS アイコンリンク                | Simple Icons + href                 |

アニメーションは `opacity` と `transform` を用いた **0.2 s フェードイン / スケール** のみに限定し、`prefers-reduced-motion` 配慮も実装する。過度な動きは排除し、ミニマル UX を保持。

## 4. GitHub Actions ワークフロー

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

## 5. フォルダ構成

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

## 6. パフォーマンス & アクセシビリティ

- 画像は `?cacheSeconds=86400` で CDN キャッシュ。
- LCP 画像は先頭に `<img loading="eager" width="100%">`。
- `aria-label` を各リンクに付与。
- Lighthouse モバイル Performance ≥ 90 を目標。

## 7. テスト計画

| 種類     | ツール        | 内容                             |
| -------- | ------------- | -------------------------------- |
| Lint     | markdownlint  | README 文法チェック              |
| ユニット | n/a           | シェルスクリプト Function テスト |
| E2E      | Lighthouse CI | LCP / a11y スコア測定            |
| Visual   | Shot-Scraper  | Diff で README 画像崩れ検知      |

## 8. 移行・拡張性

- なし

---

以上。設計変更があれば本書を更新する。
