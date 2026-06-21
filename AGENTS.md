# KATAKATA INVADERS — Codex Context

## プロジェクト概要
ポートフォリオ兼営業用LP。インベーダーゲーム風UIで手作業タスクを「撃ち落とす」演出でサービスを紹介。

## スタック
- React 18 + TypeScript + Vite
- Tailwind CSS 3.4.1 (arcade-* カラー定義済み)
- Google Fonts: Press Start 2P / DotGothic16
- Parcel でバンドル → bundle.html 出力

## ビルドコマンド
- 開発: pnpm dev
- 型チェック: pnpm tsc --noEmit --ignoreDeprecations 6.0
- ビルド: pnpm build
- バンドル: bash /path/to/bundle-artifact.sh

## 修正してはいけないファイル
- src/components/ui/* (shadcn/ui プリセット)
- calendar.tsx と resizable.tsx には @ts-nocheck 済み（意図的）

## CTAリンク管理
src/config/links.ts で一元管理。'#'はdisabled表示。

## カラーパレット（tailwind.config.js）
- arcade-green #00FF41  → GAS・クリア済み
- arcade-cyan  #00D4FF  → AI・ハイライト
- arcade-yellow #FFE600 → プレイヤー・CTA
- arcade-red   #FF3355  → 敵タスク
- arcade-orange #FF9900 → LP/SNS
