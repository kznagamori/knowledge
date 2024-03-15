# Windowsを使う上でのTips

## コマンドプロンプトを表示しないでバッチファイルを実行する
以下の.vbsファイルを作成して、それを実行する
```vbs
Set ws = CreateObject("Wscript.Shell")
ws.run "cmd /c <バッチファイルパス>", vbhide
```

## VSCodeでSSHでのリモートのワークスペースを開く
`C:\Users\<ユーザ名>\.ssh\config` にSSHの接続設定を追記する
```
Host <設定名>
    HostName <IPアドレス>
    User <SSHのユーザ名>
    Port 22
```

以下のバッチファイルを作成して、それを実行する
```
@ECHO OFF
code --file-uri "vscode-remote://ssh-remote+<設定名>/<ワークスペースの絶対パス>"
EXIT
```