# Decisions

## 2026-06-22

- `src/` と `package.json` が存在しないため、正本は `katakata-invaders.html` と判断した。
- 既存HTMLを削除せず、新しいポートフォリオ用画面を追加し、旧LPセクションはCSSで非表示にした。
- 画面遷移は hash route 風の page view 切り替えを採用した。
- 外部AI APIは使わず、チャットボットはフロントだけのルールベース診断にした。
- CTAリンクは単体HTML内の `LINKS` 定数管理を維持した。
- 公開前修正でLINE CTAのみ有効化し、未設定CTAは `href` を外して `aria-disabled="true"` のままにした。
- 追加修正でEメールCTAを `mailto:fornus.fujiwara@gmail.com` として有効化した。
- PC表示は1画面固定ではなく、内容が切れないことを優先して縦スクロール可能にした。
- 旧LPと旧ゲームJSは残すが、`portfolio-mode` では旧ゲームのキーイベントと旧Canvasループを実行しない。
