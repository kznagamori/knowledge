# Pythonでの開発準備

## 1. 標準のPythonを使用する場合
### 1.1. Pythonのインストール
```bash
$ pyenv install -l
Available versions:
  3.8.1
  3.8.2
  3.8.3
  3.8.4
  3.8.5
  3.8.6
  3.8.7
  3.8.8
  3.8.9
  3.8.10
  3.8.11
  3.8.12
  3.8.13
  3.9.0
  3.9-dev
  3.9.1
  3.9.2
  3.9.4
  3.9.5
  3.9.6
  3.9.7
  3.9.8
  3.9.9
  3.9.10
  3.9.11
  3.9.12
  3.9.13
  3.10.0
  3.10-dev
  3.10.1
  3.10.2
  3.10.3
  3.10.4
  3.10.5
  3.10.6
  3.11.0rc1
  3.11-dev
  3.12-dev
$ pyenv install 3.9.13
```

### 1.2. 使用するバージョンの設定

pyenvで使用するバージョンを設定します。
```bash
$ pyenv versions
  system
  3.7.13
* 3.8.13
  3.9.13
$ pyenv local 3.9.13
$ pyenv rehash
```

### 1.3. 仮想環境の作成
pythonコマンドで仮想環境を作成します。

#### Windows環境
```bash
$ python -m venv <仮想環境パス> --without-pip
$ <仮想環境パス>\Scripts\Activate
(<仮想環境ディレクトリ名>) $ python -m ensurepip --upgrade --default-pip
(<仮想環境ディレクトリ名>) $ python -m pip install --upgrade pip
```

以降プロジェクトで作業する場合、`<仮想環境パス>\Scripts\Activate`を行って仮想環境で作業を行うこと。

### WSL・Linux環境
```bash
$ python -m venv <仮想環境パス> --without-pip
$ source <仮想環境パス>/bin/activate
(<仮想環境ディレクトリ名>) $ python -m ensurepip --upgrade --default-pip
(<仮想環境ディレクトリ名>) $ python -m pip install --upgrade pip
```

以降プロジェクトで作業する場合、`source <仮想環境パス>/bin/activate`を行って仮想環境で作業を行うこと。

### 組み込みボード環境
```bash
$ python3 -m venv <仮想環境パス> --without-pip
$ source <仮想環境パス>/bin/activate
(<仮想環境ディレクトリ名>) $ python3 -m ensurepip --upgrade --default-pip
(<仮想環境ディレクトリ名>) $ python3 -m pip install --upgrade pip
```
以降プロジェクトで作業する場合、source <仮想環境パス>/bin/activateを行って仮想環境で作業を行うこと。


## 2. Anacondaを使用する場合
### 2.1. anacondaのインストール
```bash
$ pyenv install --l | grep anaconda
  anaconda3-2020.02
  anaconda3-2020.07
  anaconda3-2020.11
  anaconda3-2021.04
  anaconda3-2021.05
  anaconda3-2021.11
  anaconda3-2022.05
$ pyenv install anaconda3-2022.05
```

### 2.2. 使用するAnacondaのバージョンを指定
```bash
$ pyenv versions
  system
  3.7.13
* 3.8.13
  3.9.13
  anaconda3-2022.05
$ pyenv local anaconda3-2022.05
$ pyenv rehash
```

### 2.3. Anaconda環境の有効化
```bash
$ eval "$(conda shell.bash hook)"
(base) $
```
あとは、Anacondaの使用法に従って操作を行います。

### 2.4. Anacondaの仮想環境を作成
```bash
(base) $ conda create -n <仮想環境名> python=3.9
Collecting package metadata (current_repodata.json): done
Solving environment: done


==> WARNING: A newer version of conda exists. <==
  current version: 4.12.0
  latest version: 4.13.0

Please update conda by running

    $ conda update -n base -c defaults conda


## Package Plan ##
...

The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    _openmp_mutex-5.1          |            1_gnu          21 KB
    ca-certificates-2022.07.19 |       h06a4308_0         124 KB
    certifi-2022.6.15          |   py39h06a4308_0         153 KB
    ld_impl_linux-64-2.38      |       h1181459_1         654 KB
    libgcc-ng-11.2.0           |       h1234567_1         5.3 MB
    libgomp-11.2.0             |       h1234567_1         474 KB
    libstdcxx-ng-11.2.0        |       h1234567_1         4.7 MB
    ncurses-6.3                |       h5eee18b_3         781 KB
    openssl-1.1.1q             |       h7f8727e_0         2.5 MB
    pip-22.1.2                 |   py39h06a4308_0         2.5 MB
    python-3.9.12              |       h12debd9_1        19.2 MB
    sqlite-3.39.2              |       h5082296_0         1.1 MB
    tk-8.6.12                  |       h1ccaba5_0         3.0 MB
    xz-5.2.5                   |       h7f8727e_1         339 KB
    ------------------------------------------------------------
                                           Total:        40.7 MB

The following NEW packages will be INSTALLED:

  _libgcc_mutex      pkgs/main/linux-64::_libgcc_mutex-0.1-main
  _openmp_mutex      pkgs/main/linux-64::_openmp_mutex-5.1-1_gnu
  ca-certificates    pkgs/main/linux-64::ca-certificates-2022.07.19-h06a4308_0
  certifi            pkgs/main/linux-64::certifi-2022.6.15-py39h06a4308_0
  ld_impl_linux-64   pkgs/main/linux-64::ld_impl_linux-64-2.38-h1181459_1
  libffi             pkgs/main/linux-64::libffi-3.3-he6710b0_2
  libgcc-ng          pkgs/main/linux-64::libgcc-ng-11.2.0-h1234567_1
  libgomp            pkgs/main/linux-64::libgomp-11.2.0-h1234567_1
  libstdcxx-ng       pkgs/main/linux-64::libstdcxx-ng-11.2.0-h1234567_1
  ncurses            pkgs/main/linux-64::ncurses-6.3-h5eee18b_3
  openssl            pkgs/main/linux-64::openssl-1.1.1q-h7f8727e_0
  pip                pkgs/main/linux-64::pip-22.1.2-py39h06a4308_0
  python             pkgs/main/linux-64::python-3.9.12-h12debd9_1
  readline           pkgs/main/linux-64::readline-8.1.2-h7f8727e_1
  setuptools         pkgs/main/linux-64::setuptools-61.2.0-py39h06a4308_0
  sqlite             pkgs/main/linux-64::sqlite-3.39.2-h5082296_0
  tk                 pkgs/main/linux-64::tk-8.6.12-h1ccaba5_0
  tzdata             pkgs/main/noarch::tzdata-2022a-hda174b7_0
  wheel              pkgs/main/noarch::wheel-0.37.1-pyhd3eb1b0_0
  xz                 pkgs/main/linux-64::xz-5.2.5-h7f8727e_1
  zlib               pkgs/main/linux-64::zlib-1.2.12-h7f8727e_2


Proceed ([y]/n)? y


Downloading and Extracting Packages
libstdcxx-ng-11.2.0  | 4.7 MB    | ########################################################### | 100%
xz-5.2.5             | 339 KB    | ########################################################### | 100%
libgcc-ng-11.2.0     | 5.3 MB    | ########################################################### | 100%
ld_impl_linux-64-2.3 | 654 KB    | ########################################################### | 100%
python-3.9.12        | 19.2 MB   | ########################################################### | 100%
libgomp-11.2.0       | 474 KB    | ########################################################### | 100%
sqlite-3.39.2        | 1.1 MB    | ########################################################### | 100%
_openmp_mutex-5.1    | 21 KB     | ########################################################### | 100%
ncurses-6.3          | 781 KB    | ########################################################### | 100%
openssl-1.1.1q       | 2.5 MB    | ########################################################### | 100%
certifi-2022.6.15    | 153 KB    | ########################################################### | 100%
pip-22.1.2           | 2.5 MB    | ########################################################### | 100%
ca-certificates-2022 | 124 KB    | ########################################################### | 100%
tk-8.6.12            | 3.0 MB    | ########################################################### | 100%
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate <仮想環境名>
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

### 2.5. Anacondaの仮想環境へ切り替え
```bash
(base) $ conda env list
# conda environments:
#
base                  *  .anyenv/envs/pyenv/versions/anaconda3-2022.05
<仮想環境名>            .anyenv/envs/pyenv/versions/anaconda3-2022.05/envs/<仮想環境名>

(base) $ conda activate <仮想環境名>
(<仮想環境名>) $
```
