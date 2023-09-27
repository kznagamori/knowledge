# anyenvを使用したpyenv環境構築

## 1. 必要なライブラリのインストール
```bash
$ sudo apt install curl file git vim  build-essential  libbz2-dev libdb-dev libreadline-dev libffi-dev libgdbm-dev liblzma-dev libncursesw5-dev libsqlite3-dev openssl libssl-dev zlib1g-dev uuid-dev tk-dev -y
```
## 2. anyenv の環境構築

### 2.1. anyenvの取得

```bash
$ git clone https://github.com/anyenv/anyenv ~/.anyenv
```

### 2.2. anyenvを環境変数に登録

#### Ubuntu で Bashを使用している場合

```bash
$ echo 'export PATH="$HOME/.anyenv/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(anyenv init -)"' >> ~/.bashrc
$ exec $SHELL -l
ANYENV_DEFINITION_ROOT(/home/hoge/.config/anyenv/anyenv-install) doesn't exist. You can initialize it by: > anyenv install --init
```

### 2.3. anyenvの初期化
```bash
$ anyenv install --init
Manifest directory doesn't exist: /home/hoge/.config/anyenv/anyenv-install
Do you want to checkout ? [y/N]: y
Cloning https://github.com/anyenv/anyenv-install.git master to /home/hoge/.config/anyenv/anyenv-install...
Cloning into '/home/hoge/.config/anyenv/anyenv-install'...
remote: Enumerating objects: 62, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 62 (delta 1), reused 1 (delta 0), pack-reused 57
Unpacking objects: 100% (62/62), 10.50 KiB | 672.00 KiB/s, done.

Completed!
```

### 2.4. anyenvでインストール可能な環境を検索
```bash
$ anyenv install --list
  Renv
  crenv
  denv
  erlenv
  exenv
  goenv
  hsenv
  jenv
  jlenv
  luaenv
  nodenv
  phpenv
  plenv
  pyenv
  rbenv
  sbtenv
  scalaenv
  swiftenv
  tfenv
```

## 3. pyenv の環境構築

### 3.1. anyenvを使用したpyenv のインストール

```bash
$ anyenv install pyenv
/tmp/pyenv.20210601015830.16393 ~
Cloning https://github.com/pyenv/pyenv.git master to pyenv...
Cloning into 'pyenv'...
remote: Enumerating objects: 19836, done.
remote: Counting objects: 100% (748/748), done.
remote: Compressing objects: 100% (259/259), done.
remote: Total 19836 (delta 471), reused 664 (delta 437), pack-reused 19088
Receiving objects: 100% (19836/19836), 4.03 MiB | 11.47 MiB/s, done.
Resolving deltas: 100% (13406/13406), done.
~

Install pyenv succeeded!
Please reload your profile (exec $SHELL -l) or open a new session.
```

### 3.2. pyenvの設定
.bashrc に以下を追記します。
```bash
export PYENV_ROOT="$HOME/.anyenv/envs/pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi

export PATH="$HOME/.anyenv/bin:$PATH"
eval "$(anyenv init -)"

alias python="python3"
alias pip="pip3"
```

設定を反映する。

```bash
$ exec $SHELL -l
```

### 3.3. pythonのインストール
インストール可能なバージョンを確認

```bash
$ pyenv install -list
```

例として3.8.10をインストールする

```bash
$ pyenv install 3.8.10
Downloading Python-3.8.10.tar.xz...
-> https://www.python.org/ftp/python/3.8.10/Python-3.8.10.tar.xz
Installing Python-3.8.10...
Installed Python-3.8.10 to /home/hoge/.pyenv/versions/3.8.10
```

## 4. aynenvのアップデート
### 4.1. anyenv-updateのインストール

```bash
$ mkdir -p $(anyenv root)/plugins
$ git clone https://github.com/znz/anyenv-update.git $(anyenv root)/plugins/anyenv-update
```

### 4.2. **envのアップデート

```bash
$ anyenv update
Updating 'anyenv'...
 |  From https://github.com/anyenv/anyenv
 |  610ce3b..5c58783  master      -> origin/master
 |  * [new branch]      bump/v1.1.6 -> origin/bump/v1.1.6
 |  * [new tag]         v1.1.5      -> v1.1.5
Updating 'anyenv/anyenv-update'...
Updating 'nodenv'...
 |  From https://github.com/nodenv/nodenv
 |  631d0b6..acf64b3  master     -> origin/master
 |  * [new branch]      depfu/update/npm/bats-1.7.0 -> origin/depfu/update/npm/bats-1.7.0
Updating 'nodenv/node-build'...
 |  From https://github.com/nodenv/node-build
 |  a8ff5436..cdcc823e  master     -> origin/master
 |  * [new branch]        depfu/update/npm/bats-1.7.0 -> origin/depfu/update/npm/bats-1.7.0
 |  * [new branch]        latest-scraped-definitions -> origin/latest-scraped-definitions
 |  * [new tag]           v4.9.87    -> v4.9.87
 |  * [new tag]           v4.9.71    -> v4.9.71
 |  * [new tag]           v4.9.72    -> v4.9.72
 |  * [new tag]           v4.9.73    -> v4.9.73
 |  * [new tag]           v4.9.74    -> v4.9.74
 |  * [new tag]           v4.9.75    -> v4.9.75
 |  * [new tag]           v4.9.76    -> v4.9.76
 |  * [new tag]           v4.9.77    -> v4.9.77
 |  * [new tag]           v4.9.78    -> v4.9.78
 |  * [new tag]           v4.9.79    -> v4.9.79
 |  * [new tag]           v4.9.80    -> v4.9.80
 |  * [new tag]           v4.9.81    -> v4.9.81
 |  * [new tag]           v4.9.82    -> v4.9.82
 |  * [new tag]           v4.9.83    -> v4.9.83
 |  * [new tag]           v4.9.84    -> v4.9.84
 |  * [new tag]           v4.9.85    -> v4.9.85
 |  * [new tag]           v4.9.86    -> v4.9.86
Updating 'nodenv/nodenv-vars'...
Updating 'pyenv'...
 |  From https://github.com/pyenv/pyenv
 |  44db3b03..a8afc611  master     -> origin/master
 |  * [new tag]           v2.2.5     -> v2.2.5
 |  * [new tag]           v2.3.0     -> v2.3.0
 |  * [new tag]           v2.3.1     -> v2.3.1
 |  * [new tag]           v2.3.2     -> v2.3.2
 |  * [new tag]           v2.3.3     -> v2.3.3
Skipping 'pyenv/python-build'; not git repo
Updating 'anyenv manifest directory'...
 |  From https://github.com/anyenv/anyenv-install
 |  d9791df..efc79ef  master     -> origin/master
```

