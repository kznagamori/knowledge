# パッケージのインストールと復元
## 1. パッケージのインストール方法
パッケージのインストールには、pipコマンドを使用する。

### 1.1. pip自体のアップデート
```bash
$ python -m pip install --upgrade pip
```

### 1.2. pipの使い方

| 実行内容 | コマンド |
| :--- | :--- |
| パッケージのインストール | `pip install <パッケージ名>` |
| バージョンを指定してライブラリのインストール | `pip install <パッケージ名>==<バージョン>`|
| パッケージのアンインストール | `pip uninstall <パッケージ名>` |
| インストール済みのパッケージの確認 | `pip list` |
| パッケージのアップグレード | `pip install --upgrade <パッケージ名>`<br>`pip install -U <パッケージ名>` |
| 最新版かチェックする | `pip list --outdated` |
| バージョンの控えを記録 | `pip freeze > requirements.txt`<br>以下が記述されたファイルが作成される<br>`numpy==1.18.1`<br> `opencv-contrib-python==4.2.0.32`<br>`opencv-python==4.2.0.32`|
| パッケージの復元 | `pip install -r requirements.txt` |
| パッケージの依存確認 | `pip show <パッケージ名>` |

### 1.3. 各種パッケージのインストール例
### OpenCVパッケージ
```bash
$ pip install opencv-python
$ pip install opencv-contrib-python
```

### tensorflow、kerasパッケージ
```bash
$ pip install tensorflow-gpu==2.0
$ pip install keras
$ pip install pillow
$ pip install scikit-learn
$ pip install matplotlib
```

## 2. pipでインストールしてないパッケージの使用方法
組み込みボード環境でpipではなく、apt-getなどでインストールしたパッケージは、仮想環境下でインストールできない。そのため、パッケージを仮想環境下のパッケージディレクトリにコピー（リンク）して使用する。

### 2.1. パッケージを検索
```bash
$ find /usr/lib/python<Version>/dist-packages -name "*<パッケージ名>*"
```

### 2.2. 仮想環境下のパッケージディレクトリにコピー（リンク）
```bash
$ cd <仮想環境パス>/lib/python<Version>/site-packages
ln -s <パッケージファイルパス> .
```

### 2.3. 例:
```bash
$ find /usr/lib/python3.6/dist-packages -type f -name "*cv2*"
/usr/lib/python3.6/dist-packages/cv2/python-3.6/cv2.cpython-36m-aarch64-linux-gnu.so
$ cd .venv/lib/python3.6/site-packages
$ ln -s /usr/lib/python3.6/dist-packages/cv2/python-3.6/cv2.cpython-36m-aarch64-linux-gnu.so cv2.cpython-36m-aarch64-linux-gnu.so
```

## 3. インストールしたパッケージのダウンロードと復元
### 3.1. インストールしたパッケージのテキスト化
```bash
$ pip freeze > requirements.txt
```

### 3.2. インストールしたパッケージのダウンロードと復元
#### 3.2.1. Linuxの場合
##### パッケージのダウンロード
```bash
$ pip download -d <保存先ディレクトリ> -r requirements.txt
```
--extra-index-urlを指定したパッケージがある場合
```bash
$ pip download -d <保存先ディレクトリ> -r requirements.txt --extra-index-url https://download.pytorch.org/whl/cu116
```
##### パッケージの復元
```bash
$ pip install <保存先ディレクトリ>
```
もしくは
```bash
$ pip install -r /path/to/requirements.txt -f file:///path/to/archive/
```

#### 3.2.2. Windowsの場合
##### パッケージのダウンロード
```bash
$ python.exe -m pip download -d <保存先ディレクトリ> -r .\requirements.txt
```
##### パッケージの復元
```bash
$ python.exe -m pip install --no-index --find-links=<保存先ディレクトリ> -r .\requirements.txt
```

