# Handover

## 現在の構成
正本はリポジトリ直下の `katakata-invaders.html`。

`#/chatbot` に「カタカタ改善診断AI」を実装している。

ナレッジは `docs/knowledge/` のMarkdownで管理している。外部AI APIは未接続で、業務説明テキスト、添付ファイル名、検索結果からルールベース診断を生成する。

診断人格は「AI改善係長」。画面内の診断結果見出しは `AI改善係長コメント` に統一している。

## 現在のチャット起動フロー
1. `#/chatbot` を開く
2. カタカタくんの起動画面が表示される
3. 近くの吹き出しが数秒ごとに切り替わる
4. カタカタくんのお腹の `ENTER` ボタンを押す
5. 診断画面が開き、初回メッセージが表示される
6. ユーザーが入力タイプを選び、作業動画 / PDF / スクショ / 業務説明テキストを入力する
7. Markdownナレッジを検索し、AI改善係長コメント、ムダ作業、属人化リスク、自動化候補、削減時間、実装難易度、見積もり目安、推奨ツール、最初にやるべき改善、類似事例、相談文コピーを表示する
8. 診断結果をコピー、LINEで相談、もう一度診断のCTAへ進める

## 主な関数
- `loadMarkdownKnowledge`: Markdownナレッジを読み込む
- `parseKnowledgeMarkdown`: frontmatterと本文を解析する
- `searchKnowledge`: ユーザー入力に近いナレッジを検索する
- `generateImprovementDiagnosis`: 業務説明、添付ファイル名、検索結果から診断結果を作る
- `generateRagAnswer`: 旧回答生成。互換用に残っている
- `initRagConsultationBot`: 起動画面、Enter開始、吹き出し、チャットUIを初期化する

## 確認済み画面
- `#/chatbot`
- `#/works`
- `#/services`

## 営業デモ向けの現在地
- 起動画面で「なにをカタカタしていますか？」を表示
- 作業動画 / PDF / スクショ / 業務説明テキストを診断材料として表示
- ファイル選択はファイル名表示のみ。実ファイルの中身解析は未実装
- PDF請求書、LINE問い合わせ、在庫、報告書、属人化、予約、日報、Excel限界の入力例を用意
- WORKSのカタカタ改善診断AIカードは目立つ表示にし、CTAは `#/chatbot`
- SERVICESのカタカタ改善診断AIカードは `まず診断してみる` で `#/chatbot` へ遷移
- トップ / メニュー / CONTACT にも `カタカタ改善診断AIを試す` CTAを追加
- OGP / meta はカタカタ改善診断AI・AI業務改善デモ向けに更新済み

## 公開前docs
- `README.md`: 概要、機能、起動方法、未実装、今後の拡張
- `docs/demo-checklist.md`: 表示確認、スマホ確認、営業デモ時の注意
- `docs/demo-script.md`: 一言説明、デモの流れ、提案トーク

## 公開準備
- GitHub Pages向けに `index.html` を追加。内容は `katakata-invaders.html` と同一
- トップURLは `/` または `/index.html`
- 診断AI直リンクは `/#/chatbot` または `/katakata-invaders.html#/chatbot`
- 次はGitHub Pages / Netlify / Vercel などで公開
- 公開後、スマホ実機で `/#/chatbot` を確認
- 公開URLを提案文・ポートフォリオ・SNS導線に使う
- その後、スクショ撮影と提案文テンプレ作成に進む

## 未実装・将来拡張
- PDFテキスト抽出
- スクショOCR
- 動画の音声・画面解析
- LLM API接続
- 診断履歴保存
- 管理画面
- 問い合わせ導線連携

## 今後のUI改善案
- 公開先URLへ配置し、`docs/demo-checklist.md` に沿って実機確認する
- カタカタくん画像に合わせて `ENTER` ボタンの位置とサイズを微調整する
- 押下時に短いキー音を追加する
- チャット開始時に画面を軽くスクロール、またはフォーカス演出を追加する
- 相談例ボタンを「現場スタッフが押しやすい大きさ」にさらに調整する
- 初回メッセージを案件別に切り替える

## Phase2候補
- ベクトルDB対応
- 類似度検索強化
- ナレッジ管理画面
- 業務改善診断
- ヒアリング質問の自動生成
- 改善提案レポートPDF出力
- LINE / Make / n8n 連携によるAIエージェント化

## 注意点
- `.env` やAPIキーはコミットしない。
- 既存の `LINKS` 管理方針を維持する。
- 既存CTAではLINEが `https://lin.ee/RnwJwMO`、Eメールが `mailto:fornus.fujiwara@gmail.com` で有効化済み。
- `src/` 構成が復活した場合は、どちらを正本にするか先に決める。
