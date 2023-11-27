# Windows Terminal
WSLを使う場合は、Windows Terminalを使うと便利です。
そのため、Windows Terminal のインストールを行います。

## 1. Windows Terminal のインストール

### 1.1. Microsoft Storeからインストール
Microsoft Store の 検索に 「Windows Terminal」と入力します。

![Microsoft Store](assets/image-f8192cf5a5b9280ddcfcc93cb1802317d9c4d8b9447a02e0872de109283cc120.png)

Windows Terminal をインストールします。

### 1.2. GitHubからインストール
**Microsoft Terminal の GitHibサイトにアクセスする。**
[Releases microsoft/terminal](https://github.com/microsoft/terminal/releases)

**WindowsTerminalのダウンロード**
Asset セクションから Microsoft.WindowsTerminal_<versionNumber>.msixbundle をダウンロードする。
![GitHub](assets/image-dde0f99b186213e65c48bbac384e7d18138d4ec918340a79e2f8870f20a865f7.png)

ダウンロードしたファイルをダブルクリックしてインストールを行います。

### 1.3. wingetでインストール
PowerShell、コマンドプロンプトに以下を入力しインストールを行う。
```PowerShell
winget install --id=Microsoft.WindowsTerminal -e
```
以下のコマンドを入力してWindow Terminalを起動します。
```PowerShell
wt
```

## 2. Windows Terminal の設定
Windows Terminal の 設定を行います。

**Windows Terminal を起動して 設定画面を開きます。**
![Setting](assets/image-aaa29793ca75c84170d98c14e1db87ed789016224bdaa73eff807b81cc9f8677.png)

**【JSON ファイルを開く】を選択してます。**
![JSON](assets/image-920eb6f0048bce114d71ac0b5f3f573be5c9d42905f1d5e0c51e3916b4ea762d.png)

**"profiles” の ”defaults” にフォント設定を追加します。**
![Profiles](assets/image-7afac93698d3e0819f8016cfe6d267bcc386210cf9e3aefd9efd87c3472e4620.png)

```
"profiles":
    {
        "defaults":
        {
        　　// Put settings here that you want to apply to all profiles.
            "font":
            {
                "face": "\uff2d\uff33 \u30b4\u30b7\u30c3\u30af"
            }
        },
        "list":
        [
```