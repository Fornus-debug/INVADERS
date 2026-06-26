# KATAKATA INVADERS / カタカタ改善診断AI

## 目的
ポートフォリオサイト内で「作業動画・PDF・スクショ・業務説明から改善ポイントを診断する」体験を見せる。

RAG機能そのものを前面に出すのではなく、製造業で改善活動を行ってきた人間が作る、実務寄りのカタカタ改善診断AIとして見せる。

## カタカタ改善診断AI
- 入力: 作業動画 / PDF / スクショ / 業務説明テキスト
- 出力: AI改善係長コメント / ムダ作業 / 属人化リスク / 自動化候補 / 削減時間の目安 / 実装難易度 / 見積もり目安 / 推奨ツール / 最初にやるべき改善 / 類似事例 / この内容で相談する / 相談文コピー
- キャラクター: カタカタくん
- 診断人格: AI改善係長
- 現状は静的HTMLのルールベースMVP。ファイル内容解析は未実装で、選択されたファイル名と業務説明テキストを診断材料として扱う。
- 営業デモとして、起動画面、入力例、診断結果カード、相談文コピー、LINE相談導線まで一画面で見せられる状態。
- 公開デモ仕上げとして、トップ / メニュー / WORKS / SERVICES / CONTACT から `#/chatbot` へ自然に遷移できるCTAを追加済み。
- `README.md`、`docs/demo-checklist.md`、`docs/demo-script.md` を追加し、URL共有・営業説明・公開前確認に使える状態。

## 現在の正本
正本はリポジトリ直下の `katakata-invaders.html`。

現状は単体HTML構成。`src/`、`package.json`、`tailwind.config.js` は作業対象として存在しないため、React / Vite構成には戻していない。

## 公開用入口
- GitHub Pagesなどの静的ホスティング向けに `index.html` を追加
- `index.html` は `katakata-invaders.html` と同一内容
- トップURLは `/` または `/index.html`
- 診断AI直リンクは `/#/chatbot` または `/katakata-invaders.html#/chatbot`

## 実装済みページ
hash route形式で以下を持つ。

- `#/home`
- `#/menu`
- `#/profile`
- `#/services`
- `#/works`
- `#/pricing`
- `#/chatbot`
- `#/contact`

## チャット起動フロー
`#/chatbot` にアクセスすると、最初にチャット入力欄ではなくカタカタくんの起動画面を表示する。

中央のカタカタくんのお腹にある `ENTER` ボタンを押すと、カタカタ改善診断AIの画面が開く。

吹き出しは数秒ごとに切り替わる。

- なにをカタカタしていますか？
- 作業の流れを書くだけでOK。
- その転記、自動化できるかも。
- Enterキーで診断する

## RAG MVP
ナレッジは `docs/knowledge/` のMarkdownで管理。

処理はHTML内で以下の責務に分離している。

- `loadMarkdownKnowledge`: Markdownナレッジ読込
- `searchKnowledge`: タイトル・本文・タグ・ツールを検索
- `generateImprovementDiagnosis`: 業務説明、添付ファイル名、検索結果から改善診断を生成
- `generateRagAnswer`: 旧RAG回答生成。互換用に残している
- `initRagConsultationBot`: 起動画面とチャットUIを初期化

外部AI APIは現時点では使わない。APIキー未設定でも、業務説明テキスト、添付ファイル名、Markdown検索結果からルールベース診断を返す。

## 次に拡張するなら
- PDFテキスト抽出
- スクショOCR
- 動画の音声・画面解析
- LLM API接続
- 診断履歴保存
- 実機ブラウザ確認または公開先への配置

## CTA管理
CTAリンクは既存HTML内の `LINKS` 定数で管理する。

`#` のリンクは準備中として無効化する方針を維持する。
