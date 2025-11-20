# 要件定義（requirements.md）

## ビジネス仮説

クリーンでレスポンシブな GitHub プロフィール（special repository README）を用意し、採用担当・OSS コミュニティ・現職メンバーなどの閲覧者に対して Web サイト代替レベルの網羅的情報を提示すれば、

- 採用候補者としての魅力度・信頼度が向上し、面談打診数が増える。
- OSS／技術コミュニティでの認知・評価が向上し、Star/Fork などのエンゲージメントが増える。

結果として、採用強化・技術ブランディング・ネットワーク拡大につながる。

## 概要

`<username>/<username>` リポジトリの README を中心に、GitHub Stats Readme などのバッジ／ウィジェットを組み合わせて以下を実装する。

- First-view で「私について」「Tech Stacks / Skills」「GitHub Stats」「Featured Repositories」「Contact / Social Links」を 1 スクロール以内に配置。
- 動的情報（GitHub Stats・Most Used Languages・Repos・Streak）は GitHub Actions で自動更新。静的情報（プロフィール文・活動履歴・外部アカウントリンク）は手動編集。
- Light Tritanopia カラーパレットを基調に、schier.co のように洗練されたミニマルデザインと Google プロダクトに匹敵する UI/UX を実装。豊富な余白・一貫したタイポグラフィ・明確な階層構造を保ちつつ、フェードインなど控えめなマイクロインタラクションを適用。完全レスポンシブ。
- ビルド時間／描画完了は 0‒5 秒以内。MIT／Apache-2.0 など寛容ライセンスのツールのみを使用。

## ユーザーストーリー

1. **採用担当として** 候補者の GitHub プロフィールを開くと、1 スクロール以内でスキルセットと最新活動が把握でき、採用面談に進みたいと感じる。
2. **OSS コミュニティメンバーとして** コントリビュータ候補を探している際に、動的に更新される貢献履歴を見て信頼できると判断し、Issue で声を掛ける。
3. **同僚として** 技術スタックを確認しプロジェクト相談の参考にする。

## 要件

### 要件 1: First-view に主要情報を集約

**ユーザーストーリー**: 採用担当が 5 秒以内にスキル・実績の概要を把握できる。

#### 受け入れ基準

1. WHEN プロフィールを開く THEN 主要 5 セクションが 1 ビューポート以内に表示される SHALL
2. GIVEN モバイル画面 WHEN 縦スクロール THEN 同様の情報が 1 回のスクロール以内で確認できる SHALL

### 要件 2: GitHub 動的統計を自動更新

**ユーザーストーリー**: OSS メンバーが最新の貢献状況を確認できる。

#### 受け入れ基準

1. GIVEN 24 時間経過 WHEN Stats バッジ生成 Action が実行 THEN README の統計が更新される SHALL
2. WHEN API rate-limit 超過 THEN Action はリトライし、README は壊れない SHALL

### 要件 3: 洗練された UI/UX & アクセシビリティ

#### ユーザーストーリー

1. 色覚異常ユーザーも違和感なく閲覧できる。
2. schier.co のように視覚的に洗練され、Google 製品のように直感的で快適な UI/UX を体験できる。

#### 受け入れ基準

1. WHEN Light Tritanopia シミュレーションを行う THEN 主要テキストと背景のコントラスト比が WCAG AA を満たす SHALL
2. WHEN アイコンにホバー THEN 過度でないアニメーションが 0.3 秒以内で再生される SHALL
3. GIVEN デスクトップとモバイル両方 WHEN ヒーローセクションを閲覧 THEN schier.co 同等以上の視覚階層（見出しサイズ・余白・タイポグラフィスケール）が維持される SHALL

### 要件 4: パフォーマンス & コスト制約

**ユーザーストーリー**: 閲覧者が待ち時間なく情報を得られ、実装者は無料枠で維持できる。

#### 受け入れ基準

1. WHEN プロフィールを開く THEN LCP が 2.5 秒以内を達成する SHALL
2. GIVEN GitHub Actions の月間実行上限 WHEN ワークフローが走る THEN 無料枠を超過しない SHALL

## KPI 設計

### 主要指標（90 日間）

- なし

### 副次指標

- なし

## 技術要件

- Node.js ≥ 18, GitHub Actions
- 使用ライブラリは MIT / Apache-2.0 ライセンス
- README は Markdown のみで構築、画像最適化は SVG / WebP
- ビルドレス。Action で Stats 画像生成のみ行う（実行時間 < 30s）

### 優先順位付き機能一覧

Week 1: ベース README + 必須 5 セクション + 基本スタイル

Week 2: GitHub Stats／Streak／Top Languages 自動更新ワークフロー

Week 3: Featured Repositories セクション & モバイル最適化

Week 4: オプションセクション（WakaTime, Latest Blog）とホバーアニメーション

## 受け入れ条件

- すべての要件の受け入れ基準を満たし、主要指標の初期値取得が可能
- README の表示崩れが主要ブラウザ（Chrome, Safari, Edge, Firefox, Mobile Safari/Chrome）で発生しない
