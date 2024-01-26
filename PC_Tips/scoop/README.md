# scoop

Windowsでパッケージ管理行ため、scoopを使用する。

## インストール
PowerShellを立ち上げて以下を入力する。
### PowerShellのバージョンが6未満の場合
```powershell
Set-ExecutionPolicy RemoteSigned -scope Process
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
scoop install git
scoop install pwsh
```

## パッケージレポジトリの追加
デフォルトではインストールできるパッケージが少ないので追加する。
```powershell
scoop bucket add extras
scoop bucket add java
```

## 使い方
| 実行内容 | コマンド |
| ---- | ---- |
| パッケージのインストール | scoop install パッケージ |
| パッケージのアンインストール | scoop uninstall パッケージ | 
| パッケージレポジトリの追加 | scoop bucket add パッケージレポジトリ |
| インストール済みパッケージの表示 | scoop list |
| パッケージの検索 | scoop search パッケージ |
| パッケージの更新情報の更新 | scoop update |
| 古いパッケージのチェック | scoop status |
| パッケージのアップデート | scoop update パッケージ |
| 全てのパッケージのアップデート | scoop update * |

## パッケージのインストール例
### JDK
```
scoop bucket add java
scoop install openjdk
```

#### バージョン13をインストールする場合
```
scoop install openjdk13
```
####  バージョンを切り替える。
```
scoop reset openjdk13
```
### graphviz
```
scoop install graphviz
```

### sakura-editor
```
scoop bucket add iyokan-jp https://github.com/tetradice/scoop-iyokan-jp

scoop install sakura-editor
```

## その他 Tips
### pwshのアップデート
```
powershell -ExecutionPolicy Bypass -command scoop update pwsh
```

### アプリケーションのインストール先
`C:\Users\<ユーザ名>\scoop\apps` にインストールされます。
