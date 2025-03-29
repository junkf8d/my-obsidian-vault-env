---
modified:
  - 2025-03-27 20:39
created: 2025-03-27
---
PC間で、ノートは同期せず設定とプラグインだけ同期するためのgitリポジトリ。
`.obsidian`と、テンプレートなどを入れるための`🪨Obsidian`フォルダのみを同期する。

センシティブな情報は双方に同期されないほう`.gitignore`はホワイトリスト方式で管理する。
端末間のノート同期にはLiveSyncとCouchDBを使う。

## フォルダ構造

- `🪨Obsidian`: Obsidianの設定用
    - `assets`: 画像やPDFなどは全部ここに入れる
    - `public`: 他のPCにも同期したいファイル
    - `templater`: 
- 📓