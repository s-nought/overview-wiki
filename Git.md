# Gitを導入しよう

## インストール

WSLでGitコマンドを実行する場合、インストール作業はとくに不要です。

WindowsでGitクライアントを利用する場合は次のツールをインストールしましょう。
* Git
* TortoiseGit

インストール手順は[こちら](https://qiita.com/SkyLaptor/items/6347f38c8c010f4d5bd2)を参考にしてください。
GitHubの説明ですが、GitLabも同様なので問題ありません。

ただし、リポジトリのURLの設定で注意する点があります。

デフォルトだとGitLabのプロジェクトトップページのURLはSSHが表示されています。

TortoiseGitには`HTTPS`のURLを設定してください。

<div align="center">
<img src="/uploads/507a2de2672c0b6ba9ffa5626bbb4c9c/image.png" width="600">
</div>

## TortoiseGitの設定と使い方(GUI操作)

## 【参考】Gitコマンドの使い方(CUI操作)

WSLを使って、コマンドラインから操作することも可能です(このやり方がGitの基本)。

|用途|コマンド|備考|
|---|---|---|
|追加|git add ファイル名|"."を指定すると新規作成・変更されたファイルを追加|
|コミット|git commit -a -m "1行コメント"|-|
|ブランチ切り替え|git checkout ブランチ名|-|
|プッシュ|git push origin ブランチ名|-|
|マージ|git merge ブランチ名|マージ後はプッシュをしないと反映されない|
|フェッチ|git fetch origin|ローカルをリモートに同期する|
|プル|git pull origin ブランチ名|マージ+フェッチ|
|クローン|git clone リポジトリのパス|cpコマンドみたいに使える|