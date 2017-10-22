**TOC**

[[_TOC_]]

# はじめに

まずやることとして、GitLabのプロジェクトリポジトリにコミットやプッシュをするため、SSH公開鍵の設定をしてもらいます。

ここではBash on Ubuntu on Windows(以下、BUW)でのやり方を紹介します。

### BUWで次のコマンドを実行します

```bash
$ ssh-keygen -t rsa
```

`~/.ssh/`配下に`id_rsa(秘密鍵)`と`id_rsa.pub(公開鍵)`が生成されます。GitLabに設定するのは`"公開鍵"`の方です。秘密鍵は秘密にしておいてください。

### 公開鍵の中身をコピーします

catコマンドでもなんでもいいので、`id_rsa.pub(公開鍵)`を開いて中身をクリップボードにコピーします。

### 公開鍵の中身をGitLabのSSH Keysに登録します

SSH Keyが設定されていない場合は、トップ画面に**`You won't be able to pull or push project code via SSH until you add an SSH key to your profile`**と表示されていると思うので、そこから設定画面に移動します。

もし表示されていなければ、画面右上のアカウントの`Settings`→`左サイドのリストのSSH Keys`で設定画面にいけます。

あとは、先程コピーした公開鍵の中身を`Key`に貼り付けてTitleを適当に入力(sshKeyとか)して`Add key`をクリックすれば完了です。

# 環境構築

# 情報共有

# Gitコマンド
