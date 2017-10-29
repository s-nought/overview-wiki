[[_TOC_]]

# はじめに

まずやることとして、GitLabのプロジェクトリポジトリにコミットやプッシュをするため、SSH公開鍵の設定をしてもらいます。

ここではWindows Subsystem on Linux(以下、WSL)でのやり方を紹介します。

## SSH公開鍵の設定

**1. WSLで次のコマンドを実行します**

```bash
$ ssh-keygen -t rsa
```

`~/.ssh/`配下に`id_rsa(秘密鍵)`と`id_rsa.pub(公開鍵)`が生成されます。GitLabに設定するのは`"公開鍵"`の方です。秘密鍵は秘密にしておいてください。

**2. 公開鍵の中身をコピーします**

catコマンドでもなんでもいいので、`id_rsa.pub(公開鍵)`を開いて中身をクリップボードにコピーします。

**3. 公開鍵の中身をGitLabのSSH Keysに登録します**

SSH Keyが設定されていない場合は、トップ画面に**`You won't be able to pull or push project code via SSH until you add an SSH key to your profile`**と表示されていると思うので、そこから設定画面に移動します。

もし表示されていなければ、画面右上のアカウントの`Settings`→`左サイドのリストのSSH Keys`で設定画面にいけます。

あとは、先程コピーした公開鍵の中身を`Key`に貼り付けてTitleを適当に入力(sshKeyとか)して`Add key`をクリックすれば完了です。

それでは素敵なGitLifeを！！

# そもそもGitって？

Gitはバージョン管理システムのことです。名前が似ていますが、GitLabはGitを利用して、管理するプロジェクト等をインターネット上に公開するWebサービスのことです。

Gitを利用することで，プロジェクトの変更履歴の記録・追跡が可能になります。プロジェクトを変更前の状態に戻したり，複数人での編集作業も可能となります。要するに，誰が何をどのように変更したのかを管理することができます。

使い方は，実際に使用して慣れる必要があります。基本的に，次の図が理解できれば十分です。
<div align="center">
<img src="/uploads/a47cc6a696c945dc127478c55b4d3295/image.png" width="400">
</div>

図の用語について少しまとめます。

|用語|説明|
|---|---|
|リモートリポジトリ|プロジェクトの大元です。|
|ローカルリポジトリ|プロジェクトメンバーの各端末にあるリポジトリです。リモートリポジトリのコピーのようなものです。自分が行った変更は必ずローカルリポジトリを通じてリモートリポジトリに反映されます。|
|ユーザー|自分のPCを想定してください。|
|コミット|自分の変更をローカルリポジトリに反映することです。|
|プッシュ|コミットした内容をリモートリポジトリに反映することです。|
|フェッチ|ローカルリポジトリを最新化することです。最新化元はリモートリポジトリです。|

それではGitを使ってみましょう。

「[Gitの環境構築](Git)」を参照して使ってみてください。

# 使ってみてよかったもの

@Ohkumaneko が使ってみてよかったものを紹介します。その時々のマイブームで更新していきますね。

## WSL(なんちゃってLinux)

WindowsのInsiderPreviewのときはBash on Ubuntu on Windowsと呼ばれていました(OSもUbuntuしかありませんでした)。現在はWindowsストアで配布されています(Ubuntu、OpenSUSE、Fedora(予定))。用途としてはWindowsのサブOS、ターミナルの代用として使っています。Tera Termと違って、シェルを使えるので便利(まぁOSなんで)。また、VirtualBoxのような仮想化ではないので、動作は非常に軽い(Dockerコンテナに近いイメージ)。ぜひ導入してみてください。

導入方法は[こちら]()を参照してください。

## Intellij(Javaのエディタ)

JavaといえばEclipse！！...の時代も終わりつつあるようです。Gitでプロジェクトを管理するケースが増え、Gitと相性のよい**Intellij**(統合開発環境)が選ばれるようになってきています(使ったことないけどEclipseはGitと相性がよくないのかな？)。また、Eclipseの場合は、先頭文字が一致していないと補完機能が動作しませんが、Intellijでは部分一致でコーディングを補完してくれます。非常に親切です。あと、個人的にはIntellijのデザインの方が好きです。

導入方法は[こちら]()を参照してください。

## Visual Studio Code(TypeScriptのエディタ)

## Angular(JavaScriptのフレームワーク)

素晴らしすぎるフレームワークです。簡単なWebアプリを作るならAngular以外に選択肢はないでしょう。習得コストは高いかもしれませんが、慣れてしまえば手放せなくなってしまうくらいです。言語はTypeScriptになります。ただ、ビルドするとJavaScriptに変換されるので、JavaScriptが動くブラウザであれば動作します。エディタはVisual Studio Codeがおすすめです。

導入方法は[こちら]()を参照してください。

## MEGAsync

## Firebase

# Gitコマンド

|用途|コマンド|備考|
|---|---|---|
|追加|`git add ファイル名`|"."を指定すると新規作成・変更されたファイルを追加|
|コミット|`git commit -a -m "一行コメント"`|-|
|ブランチ切り替え|`git checkout ブランチ名`|-|
|プッシュ|`git push origin ブランチ名`|-|
|マージ|`git merge ブランチ名`|マージ後はプッシュをしないと反映されない|
|フェッチ|`git fetch origin`|ローカルをリモートに同期する|
|プル|`git pull origin ブランチ名`|マージ+フェッチ|
|クローン|`git clone リポジトリのパス`|cpコマンドみたいに使える|

# Markdown記法

GitLabのMarkdownの書き方については[ここのドキュメント](https://docs.gitlab.com/ee/user/markdown.html)を参照。

## 数式を書く

GitLabでは$`\KaTeX`$のコマンドが利用できるみたいです。

使えるコマンドについては[ここ](https://khan.github.io/KaTeX/function-support.html)を参照してください。

### 文中に数式を書く
<pre>
文中に $`e^{i x} = \cos{x} + i \sin{x}`$ のように数式を書ける。
</pre>

### 独立した行に数式を書く
<pre>
```math
\zeta(s) = \sum_{n \in \mathbb{N}} \frac{1}{n^s}
```
</pre>
```math
\zeta(s) = \sum_{n \in \mathbb{N}} \frac{1}{n^s}
```

### 独立した行に**複数行**の数式を書く

式番号の付け方はよくわからない。。。できないのかな？

<pre>
```math
\begin{aligned}
ax^2 + bx + c &= 0 \\
x &= \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{aligned}
```
</pre>
```math
\begin{aligned}
ax^2 + bx + c &= 0 \\
x &= \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{aligned}
```

### 数学の記事を書いてみた

* [フェルミ推定](Fermi)
* [オイラーの公式](Euler_formula)