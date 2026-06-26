# カタカタ改善診断AI / Fornus Portfolio

## 概要

作業動画・PDF・スクショ・業務説明から、ムダ作業・属人化リスク・自動化候補・削減時間・実装難易度・見積もり目安を診断するWebデモ。

## 主な機能

- カタカタくんによる案内
- AI改善係長による診断コメント
- 業務説明テキスト診断
- ファイル名添付表示
- ルールベース診断
- 類似事例表示
- 診断結果コピー
- LINE相談導線

## 現在の仕様

静的HTMLのMVP。
ファイル本文解析、OCR、動画解析、LLM API連携は未実装。

## 起動方法

```bash
python -m http.server 8080
```

URL:

```text
http://localhost:8080/
http://localhost:8080/index.html
http://localhost:8080/katakata-invaders.html
http://localhost:8080/katakata-invaders.html#/chatbot
http://localhost:8080/#/chatbot
```

## 公開方法

### GitHub Pages

1. GitHubにpush
2. Repository Settings を開く
3. Pages を開く
4. Source を `Deploy from a branch` にする
5. Branch を `main`、folder を `/root` にする
6. 公開URLを確認する

公開後の確認URL例:

```text
https://ユーザー名.github.io/リポジトリ名/
https://ユーザー名.github.io/リポジトリ名/#/chatbot
```

## 今後の拡張

- PDF本文抽出
- スクショOCR
- 動画の音声・画面解析
- LLM API連携
- 診断履歴保存
- 管理画面
- 問い合わせ送信連携
