# Windowsを使う上でのTips

## コマンドプロンプトを表示しないでバッチファイルを実行する
以下の.vbsファイルを作成して、それを実行する
```vbs
Set ws = CreateObject("Wscript.Shell")
ws.run "cmd /c <バッチファイルパス>", vbhide
```
