# pyenvの使い方

## 基本操作

| 実行内容 | コマンド |
| :--- | :--- |
| インストール可能なPythonバージョンのリスト | `pyenv install --list` |
| インストール | `pyenv install <version>`<br>※64bitは\<version\>-amd64 |
| インストール済みバージョンのリスト | `pyenv versions` |
| 全体のバージョンの切り替え | `pyenv global <version>` |
| ローカルフォルダーのバージョンの切り替え | `pyenv local <version>` |
| バージョン切り替えの反映 | `pyenv rehash` |
