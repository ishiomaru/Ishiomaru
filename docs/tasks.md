# 実装計画

- [ ] **1. Week 1 – ベース README & 基本レイアウト**
- [x] 1.1 `README.md` テンプレート作成

  - [x] セクション配置: About / Tech Stacks / GitHub Stats / Featured Repos / Contact
  - _要件: 1.1_

- [x] 1.2 レスポンシブレイアウト実装（≤480 px 縦積み）

  - [x] モバイル表示で 1 スクロール以内に主要 5 セクションを確認
  - _要件: 1.2_

- [x] 1.3 Light Tritanopia カラーパレット適用

  - [x] SCSS 変数定義 `--bg` `--fg` `--accent` `--secondary`
  - _要件: 3.1_

- [x] 1.4 基本スタイル & Markdownlint 設定

  - [x] `markdownlint` 設定を追加し CI 取込準備
  - _要件: 3.1_

- [x] 1.5 デザイントークン & Typographic Scale 実装

  - [x] `style` ブロックに `space-*, font-*` 変数を定義し README に適用
  - [x] `Inter`, `Noto Sans JP` を読み込み、見出しサイズをスケール (1.25) で設定
  - _要件: 3.3_

---

- [ ] **2. Week 2 – GitHub Stats 自動更新ワークフロー**
- [ ] 2.1 `update-stats.yml` ワークフロー作成

  - [ ] 毎日 03:00 UTC 実行、Stats 画像を `/assets` に出力
  - _要件: 2.1_

- [ ] 2.2 Rate-limit リトライ導入

  - [ ] `max-attempts: 3` & 30 m インターバル
  - _要件: 2.2_

- [ ] 2.3 assets ディレクトリ追加と git 自動コミット

  - [ ] `git add ./assets && git commit -m "chore: update stats images"`
  - _要件: 2.1_

---

- [ ] **3. Week 3 – Featured Repos & パフォーマンス最適化**
- [ ] 3.1 `RepoCard` コンポーネント実装

  - [ ] GitHub API で Star / Lang / Desc を取得し SVG 生成（3 件）
  - _要件: 1.1_

- [ ] 3.2 Lighthouse モバイル Performance ≥ 90 達成

  - [ ] LCP ≤ 2.5 s を検証
  - _要件: 4.1_

- [ ] 3.3 aria-label 追加 & カラーコントラスト確認

  - [ ] `axe-core` で自動テスト
  - _要件: 3.1_

- [ ] 3.4 視覚階層 / 余白検証 & 調整

  - [ ] デスクトップ・モバイルで schier.co 同等の見出しサイズ・余白を確認
  - [ ] README 内スタイルを調整し `lighthouse` + スクリーンショット比較で検証
  - _要件: 3.3_

---

- [ ] **4. Week 4 – オプションセクション & 仕上げ**
- [ ] 4.1 WakaTime セクション追加（任意）

  - [ ] REST API で直近 7 日グラフを SVG 埋め込み
  - _要件: 1.1_

- [ ] 4.2 Latest Blog セクション追加（任意）

  - [ ] RSS → JSON 変換で最新 3 件リンク
  - _要件: 1.1_

- [ ] 4.3 アイコンホバーアニメーション実装

  - [ ] `transition: transform 0.2s` で scale-up
  - _要件: 3.2_

- [ ] 4.4 最終 QA / ブラウザ互換テスト

  - [ ] Chrome / Safari / Firefox / Edge / iOS / Android
  - _要件: 4.2_

---

- [ ] **5. クロスカットタスク**
- [ ] 5.1 CI → markdownlint + Lighthouse CI

  - _要件: 4.1, 3.1_

- [ ] 5.2 ドキュメント更新 (`docs/*.md`)

  - _要件: 全般_

- [ ] 5.3 リリースノート作成 & タグ付け

  - _要件: 全般_
