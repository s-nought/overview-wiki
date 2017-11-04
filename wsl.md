# Windows Subsystem for Linux(WSL)を導入しよう

**導入要件**

|OS|バージョン|リリース|コードネーム的なやつ|
|:-:|:-:|:-:|:-:|
|Windows10|1709|2017/10/17|Fall Creators Update|

`Windows10`を前提としています。(それ以外ではWSLは使えません。。。)



## インストール

InsiderPreviewのときとは違って、導入は非常に楽になりました。単にMicrosoftのストアから取得するだけです。

ただ、WSLはデフォルトでは有効になっていないので、まずはWSLの機能を有効にします。

次の手順に従ってください。(2通りあります)

### 設定から機能を有効にする方法

1. 「Winキー」＋「I」で設定を開く
1. 「アプリ」を開く
1. 右側の関連設定の「プログラムと機能」を開く
1. 左側の「Windowsの機能の有効化または無効化」を開く
1. 「Windows Subsystem for Linux」にチェックを入れて再起動する

### PowerShellのコマンドから機能を有効にする方法

「Windows PowerShell」を`管理者権限`で開いて次のコマンドを実行する。

```powershell
PS C:\WINDOWS\system32> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

コマンド実行後、再起動する。

### ストアからダウンロード

WSLの機能を有効化して再起動したら、アプリをダウンロードします。

ストアを開いて「wsl」と検索するとそれっぽいアプリが見つかります。あとは好きなディストリビューションを選びます。

ダウンロード完了後、アプリを起動します。起動すると、インストールが開始されてユーザー名・パスワードの設定を求められます。このアカウントはWindowsのアカウントとは別のものなので、任意のものを設定できます。

インストールはこれでおしまい。あとは自由に設定をします。

環境をもとに戻したい(初期化したい)場合はアプリをアンインストールして、再インストールします。アンインストールするとホームディレクトリも削除されるので、必要であれば適宜バックアップをしましょう。

## 設定(Ubuntuの場合)

### rootのパスワード設定

次のコマンドを実行して、任意のパスワードを設定する。

```bash
$ sudo password root
```

### 日本語化

1. 言語パッケージをインストールする。

```bash
$ sudo apt install language-pack-ja
```

2. /etc/default/localeの言語設定を変更する。

```bash
$ sudo update-locale LANG=ja_JP.UTF-8
```