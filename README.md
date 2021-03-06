# dotfiles for designers (仮)

## インストール

### 各種ファイルのセットアップ

```
git clone https://github.com/fact-real/dotfiles-for-designers.git ~/dotfiles
cd ~/dotfiles
sh setup.sh
```

以下の処理を行います:

* 各種ファイルのシンボリックリンクを作成
* vim のプラグインマネージャーである vundle を clone

### zsh のセットアップ

ユーザーのデフォルトシェルを zsh に変更します。
変更後、ログインし直してください。

```
su -
chsh -s /usr/local/bin/zsh user
```

### vim のセットアップ

プラグインのインストール:

```
vim +BundleInstall
```

### git のセットアップ

`~/.gitconfig.local` を編集する:

* コミットコメントで使用されるメールアドレスと名前

```
[user]
    email = username@example.com
    name = username
```

### ssh のセットアップ

```
mkdir ~/.ssh
cp ~/dotfiles/samples/.ssh/config.sample ~/.ssh/config
```

`~/.ssh/config` を編集する:

初期状態では GitHub についての設定がされています。
秘密鍵を ~/.ssh/id_rsa.github.com に置くと、 GitHub に ssh できるようになります。

## 各種ツールのカスタマイズ内容やコマンドなどについての説明

### zsh

### git

* `glo/git log`: コミットログを参照
* `gco/git co/git checkout`
* `gci/git ci/git commit`: コミット

#### git hooks

`samples/git/hooks` 以下に hook を置いています。

リポジトリごとに hook を設定する必要があります。
ファイルをコピーするか、シンボリックリンクを張ると良いでしょう:

```
ln -s ~/dotfiles/samples/git/hooks/[hook のファイル名] [リポジトリのパス]/.git/hooks/
```

* **prepare-commit-msg** : コミットコメントを入力する時に、ブランチ名のチケット番号を自動で入力します。

### vim

* NERDTree: ファイラ。F2 キーで起動する
* grep.vim: `:Rgrep` コマンドで grep を行う

#### 補完について

対応しているファイルフォーマットでは補完が使用できます

* Ctrl-p/Ctrl-n で候補を選択
* Ctrl-k で候補を決定

#### プラグインについて

プラグインのマネージャーに [Vundle](https://github.com/gmarik/vundle) を使用しています

* `BundleInstall`: `.vimrc` に追加したプラグインのインストール
* `BundleClean`: `.vimrc` から削除したプラグインのアンインストール
* `BundleInstall!`: プラグインのアップデート

## 動作環境

以下の環境で確認しています

* zsh 5.0.x
* vim 7.3.x
* git 1.8.x
* tmux 1.8
