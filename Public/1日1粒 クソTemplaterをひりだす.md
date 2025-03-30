---
created: 2025-03-28T20:32:35
modified:
  - 2025-03-31T00:53:50
  - 2025-03-29T20:15:58
  - 2025-03-28T21:03:39
  - 2025-03-28T20:39:55
aliases: 
tags: 
related: 
memo: 
---

zenn: [Obsidian 1日1粒、クソTemplaterを作りたい場所](https://zenn.dev/junkf8d/scraps/efaea9d02ea1e5)

[[Templater]]良すぎる
色々とちょうどいいい

## 書きたい

- QRコード
- Termuxと連携
    - スマホの位置情報
    - スマホのスクショ
        - スクショはadb使わないとむずいかも
            - adb使えばいいのでは？
    - スマホのカメラ
    - 課題:
        - テザリングでもやりたい
            - IPどうすんの？
        - 環境変数は読めるのか？
            - コマンドにパスは通っている？
            - .ssh/configは読める？
- シェル
- ネット
    - 位置情報
    - API
    - 
- PC情報
    - スペック
    - カメラ
    - どれだけ使ってるか
    - 今の状態
    - OS情報
- 文字列の置換
    - 英数字を変換
    - 自宅からの距離

## Templaterの課題・疑問

- いちいちファイル用意して登録するのがめんどい
    - JavaScriptファイル作成すんのめんどい
        - フォルダ内のやつ全部読み込んでくれればいいのに？
            - 読み込んでくれたところでホットキーに追加するのは手動
    - 選択項目から選ばせる suggester
        - https://silentvoid13.github.io/Templater/internal-functions/internal-modules/system-module.html#tpsystemsuggestertext_items-string--item-t--string-items-t-throw_on_cancel-boolean--false-placeholder-string---limit-number--undefined
- jsのライブラリ読めるのか？
    - QRコードのライブラリとか使いたいけど
    - チャートのライブラリとか使えるなら何でもありでは？