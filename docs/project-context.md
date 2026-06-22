# KATAKATA INVADERS / Fornus Portfolio Context

## 正本

現時点の正本は `katakata-invaders.html` です。
`src/`、`package.json`、`tailwind.config.js`、`bundle.html` はこの作業時点では存在しません。

## 目的

KATAKATA INVADERS の世界観を残しつつ、Fornus のポートフォリオ入口として一瞬で分かる構成にする。

## 現在の構成

- 単体HTML
- hash route 風の画面切り替え
- `#/home`
- `#/menu`
- `#/profile`
- `#/services`
- `#/works`
- `#/pricing`
- `#/chatbot`
- `#/contact`

## CTA管理

単体HTML内の `LINKS` 定数で管理します。
`#` の場合は準備中として無効化します。
