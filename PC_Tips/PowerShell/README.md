# PowerShell

## 設定確認
### 初期実行権限確認

```powershell
PS C:\> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned

```

### 環境変数確認
```powershell
PS C:\> Get-ChildItem env:
```

### パス確認
```powershell
PS C:\> Get-Item Env:Path | Format-Table -AutoSize -Wrap
```

## 設定変更
### 環境変数設定
```powershell
PS C:\> Set-Item Env:Hoge "Hoge"
```

### パス設定
```powershell
PS C:\> $path = [Environment]::GetEnvironmentVariable("PATH", "User")
PS C:\> $path = "追加するパス" + $path
PS C:\> [Environment]::SetEnvironmentVariable("PATH", $path, "User")
```

## コマンド実行
### 管理者権限なしでスクリプトを実行する
```powershell
PS C:\> powershell -ExecutionPolicy Bypass -command スクリプト
```

### 管理者権限で起動
```powershell
PS C:\> start pwsh -verb runas
```

### 基本的なコマンドレット
| 操作 | コマンドレット | エイリアス |
| ---- | ---- | ---- |
| フォルダの内容一覧 | Get-ChildItem | dir, ls |
| 場所を移動する。 | Set-Location | cd, chdir |
| 文字列を表示する。 | Write-Host, Write-Output | echo |
| テキストファイルの内容を表示する。| Get-Content | type, cat |
| ファイルのコピー | Copy-Item | copy, cp |
| ファイルの削除 | Remove-Item | del, rm |
| ファイルのリネーム | Rename-Item | ren, mv |
| ディレクトリの作成 | New-Item | md, mkdir |
| ディレクトリの削除 | Remove-Item | rd, rmdir |
| 履歴の表示 | Get-History | history |
| 履歴コマンドの実行 | Invoke-History | F7キー |
| エイリアスの表示 | Get-Alias | alias |
| ヘルプの表示 | Get-Help | help |
| 画面のクリア | Clear-Host | cls |


## PowerShell Core
PowerShellを起動すると以下のメッセージがでる。
```powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

新しいクロスプラットフォームの PowerShell をお試しください https://aka.ms/pscore6
```

### インストール
[Scoop](../scoop/README.md) を使用してpwshをインストールする
もしくは、以下のサイトにアクセスして、環境用のPower Shell Coreをインストールします。
[GitHub - PowerShell/PowerShell: PowerShell for every system!](https://github.com/PowerShell/PowerShell#-powershell)

## PowerShellスクリプトの実行ポリシー
 | 実行ポリシー | 署名付き | 署名なし／ローカル | 署名なし／非ローカル | 概要 |
| ---- | ---- | ---- | ---- | ---- |
| Restricted | × | × | × | 全てのスクリプトが実行禁止。PowerShellまたはWindows OSインストール直後のデフォルト設定（Windows Server 2012 R2を除く）|
| AllSigned | ○ | × | × | 署名されているスクリプトのみが実行可能。署名されていないスクリプトは実行禁止 |
| RemoteSigned | ○ | ○ | × | ローカルに保存されているスクリプトは実行可能。インターネットからダウンロードしたスクリプト（非ローカルのスクリプト）は、署名されているもののみが実行可能。Windows Server 2012 R2では、この設定がデフォルト |
| Unrestricted | ○ | ○ | △ | 全てのスクリプトが実行可能。ただしインターネットからダウンロードしたスクリプトは、実行するかどうかが確認されるので、ユーザーが明示的に許可した場合のみ実行される |
| Bypass | ○ | ○ | ○ | 警告やユーザーへの確認なしに、全てのスクリプトが実行可能 |

### 実行ポリシーの設定
```powershell
Set-ExecutionPolicy 実行ポリシー
```

### PowerShell の起動時に実行ポリシーを指定する(管理者権限不要)
PowerShell の起動引数 `-ExecutionPolicy` で実行ポリシーの指定ができます。

### コマンドプロンプトから起動
1. コマンドプロンプトを起動します。
2. 次のコマンドを実行します。
※Unrestricted の部分は 表「実行ポリシーの種類」を参考に、適切なポリシーを指定します。
```powershell
PowerShell.exe -ExecutionPolicy Unrestricted
```
3. スクリプトが実行可能な状態で PowerShell が起動します。

### ショートカットから起動
1. PowerShellのショートカットを作成します。
2. ショートカット の プロパティを表示し、リンク先欄に 起動引数を追加します。
※Unrestricted の部分は 表「実行ポリシーの種類」を参考に、適切なポリシーを指定します。
```
-ExecutionPolicy Unrestricted
``` 

## 履歴表示設定
powershellの設定ファイルを作成する。
```powershell
$profile
New-Item -Path $Profile -ItemType file -force
Notepad $profile
```
以下の内容を設定ファイルに追記する。
```
### peco settinng
Set-PSReadLineKeyHandler -Chord Ctrl+r -ScriptBlock {
    $command = Get-Content (Get-PSReadLineOption).HistorySavePath | peco --select-1 --on-cancel error
    if (-not $command) {
        return
    }
    [Microsoft.PowerShell.PSConsoleReadLine]::InvokePrompt()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert($command)
}

## input History Plugin settinng
Set-PSReadLineOption -PredictionSource HistoryAndPlugin
Set-PSReadLineOption -PredictionViewStyle ListView
Set-PSReadLineOption -Colors @{ InLinePrediction = [ConsoleColor]::Cyan }
```
