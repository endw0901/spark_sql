# HDFSシェルコマンド

- http://www.mwsoft.jp/programming/hadoop/hdfs_shell.html

- HDFSのファイル表示など
- sparkで読むまえにHDFSファイルを見てスキーマを確認するときなど

```
hadoop fs -ls /user/input

hadoop fs -cat /user/inputfile.csv | head -10
```
