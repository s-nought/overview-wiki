# Windows Subsystem for Linux(WSL)を導入しよう

**導入要件**

OS|バージョン|リリース|コードネーム的なやつ
:-:|:-:|:-:|:-:
Windows10|1709|2017/10/17|Fall Creators Update

`Windows10`を前提としています。(windows10以外のOSまたは導入要件以前のバージョンのWindows10では、WSLは使えません。。。)

## インストール

InsiderPreviewのときとは違って、導入は非常に楽になりました。単にMicrosoftのストアから取得するだけです。

ただ、WSLはデフォルトでは有効になっていないので、まずはWSLの機能を有効にします。

次の手順に従ってください。(2通りあります)

### 【方法1】設定から機能を有効にする方法

1. 「Winキー」＋「I」で設定を開く
1. 「アプリ」を開く
1. 右側の関連設定の「プログラムと機能」を開く
1. 左側の「Windowsの機能の有効化または無効化」を開く
1. 「Windows Subsystem for Linux」にチェックを入れて再起動する

### 【方法2】PowerShellのコマンドから機能を有効にする方法

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

# Ubuntu編

WSLのUbuntuを導入した際の推奨設定について記載します。

## 各種設定

### rootのパスワード設定

次のコマンドを実行して、任意のパスワードを設定する。

```bash
$ sudo password root
```

### いろいろ最新化する

```bash
$ sudo apt-get update
$ sudo apt-get upgrade
```

### 日本語化

言語パッケージをインストールする。

```bash
$ sudo apt install language-pack-ja
```

/etc/default/localeの言語設定を変更する。

```bash
$ sudo update-locale LANG=ja_JP.UTF-8
```

### viの設定

コメントのハイライトを変更(デフォルトだと見づらいため)、行番号を表示する。

`/etc/vim/vimrc`に以下を追加

```
highlight Comment ctermfg=darkgrey
set number
```

### Gitの最新化

デフォルトのリポジトリではGitのバージョンが古いため、リポジトリを変更する。

```bash
$ sudo add-apt-repository ppa:git-core/ppa
```

パッケージの更新をする。

```bash
$ sudo apt-get update
$ sudo apt-get upgrade
```

これでGitが最新化されるはず。

※Gitのバージョン確認方法

```bash
$ git --version
```

### OS(Ubuntu)をLTS版から通常版にアップグレード(2018/04/15現在：不安定になるのでやらない方がいい。。。)

設定ファイルを修正する。

次のコマンドで設定ファイルを開き、「Prompt=lts」→「Prompt=**normal**」に変更する。

```bash
sudo vim /etc/update-manager/release-upgrades
```

OSのリリースバージョンを更新する。

```bash
$ sudo do-release-upgrade
```

バージョンの確認

```bash
$ lsb_release -a
```

# Debian編

WSLのDebianを導入した際の推奨設定について記載します。

※UbuntuはDebianから派生したディストリビューションであるため、各種設定方法は基本的にUbuntuと同様の手順となります。

## 各種設定

### viの設定

Ubuntuと違い、viのキーバインドが昔の設定となっているため、デフォルトでは矢印キーによるカーソル移動やバックスペースで文字削除ができません。Ubuntu同様の操作感にするためには次を設定します。

viの設定ファイルを作成し、編集する。

```bash
$ touch ~/.vimrc
$ vi ~/.vimrc
```

.vimrcファイルに次を記載して保存する。

```bash
set nocompatible
set backspace=indent,eol,start
```

ターミナルを閉じて再起動すれば設定が読み込まれる。

※rootについても同様に設定ファイルを作成しないと、rootでキーバインドがデフォルトのままになります。

### 日本語化

Ubuntuと実行コマンドが異なります。

日本語関連パッケージをインストールする。

```bash
$ sudo apt -y install task-japanese locales-all
```

以下のファイルを`root`ユーザーで編集する。

```bash
# vi /etc/default/locale
```

以下を設定して保存する。

```bash
LANG=ja_JP.UTF-8
LANGUAGE="ja_JP:ja" 
```

ターミナルを閉じて再起動すれば日本語化される。

### llコマンドを設定

Debianではデフォルトでllコマンドを使用することができないため、エイリアスを設定する。

以下のファイルを編集する。

```bash
$ vi .bashrc
```

以下を追記して保存する。

```bash
alias ll='ls -la'
```

ターミナルを閉じて再起動すれば設定が読み込まれる。

### パッケージの更新

Ubuntu同様、aptコマンドを利用する。

とりあえず、次のコマンドを実行することで、全パッケージの更新および不要パッケージの削除を行うことができる。

```bash
$ sudo apt-get update -y
$ sudo apt-get upgrade -y
$ sudo apt-get dist-upgrade -y
$ sudo apt-get autoremove -y
$ sudo apt-get autoclean -y
```