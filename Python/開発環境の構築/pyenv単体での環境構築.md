# pyenv単体での環境構築

## 1. Windows環境
Windows での pyenv の環境構築には [pyenv-win](https://github.com/pyenv-win/pyenv-win) を使用します。
ターミナルにはPowerShell6以上を使用します。

### 1.1. pyenv-winのインストール
gitを使用してインストールします。PowerShellを立ち上げて以下を入力します。

```powershell
PS > git clone https://github.com/pyenv-win/pyenv-win.git "$HOME\.pyenv"
PS > [environment]::SetEnvironmentVariable("PYENV", "$env:USERPROFILE\.pyenv\pyenv-win", "User")
PS > $path = [Environment]::GetEnvironmentVariable("PATH", "User")
PS > $path = "$env:USERPROFILE\.pyenv\pyenv-win\bin;$env:USERPROFILE\.pyenv\pyenv-win\shims;" + $path
PS > [environment]::SetEnvironmentVariable("Path", $path, "User")
```

## 1.2. Pythonをインストールする

PowerShellを再起動する。
以下のコマンドでインストール可能なバージョンが確認できる。

```powershell
PS > pyenv install --list | Sort-Object
3.7.6
3.7.6-amd64
3.8.0
3.8.0a1
3.8.0a1-amd64
3.8.0a2
3.8.0a2-amd64
3.8.0a3
3.8.0a3-amd64
3.8.0a4
3.8.0a4-amd64
3.8.0-amd64
3.8.0b1
3.8.0b1-amd64
3.8.0b2
3.8.0b2-amd64
3.8.0b3
3.8.0b3-amd64
3.8.0b4
3.8.0b4-amd64
3.8.0rc1
3.8.0rc1-amd64
3.8.1
3.8.1-amd64
```

例として3.7.6をインストールする

```powershell
PS > pyenv install 3.7.6-amd64
```

## 2. Linux環境

### 2.1. pyenv のインストール
githubからリポジトリをcloneします。
```bash
 $ git clone https://github.com/pyenv/pyenv.git ~/.pyenv
```

### 2.2. pyenvの設定
.bashrc に以下を追記します。

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi

alias python="python3"
alias pip="pip3"
```

## 3. 組み込みボード
組み込みボードでは、用意されているPythonを使用します。
Python3と必要なライブラリのインストールを行います。

```bash
$ sudo apt install build-essential gfortran hdf5-tools libatlas-base-dev libblas3 libblas-dev libbz2-dev libdb-dev libffi-dev libgdbm-dev libhdf5-dev libhdf5-serial-dev libhdf5-103 libjpeg-dev liblapack3 liblapack-dev liblzma-dev libncurses5-dev libreadline-dev libsqlite3-dev libssl-dev python3 python3-dev python3-pip python3-venv tk-dev uuid-dev zip zlib1g-dev
```

