# HDFSシェルコマンド

- http://www.mwsoft.jp/programming/hadoop/hdfs_shell.html

- HDFSのファイル表示など
- sparkで読むまえにHDFSファイルを見てスキーマを確認するときなど

```
hadoop fs -ls /user/input

hadoop fs -cat /user/inputfile.csv | head -10
```

## hadoop fsとhdfs dfs

- 違いがない。同じらしい
- https://www.it-swarm.dev/ja/hadoop/%E3%80%8Chadoop-fs%E3%80%8D%E3%82%B7%E3%82%A7%E3%83%AB%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%A8%E3%80%8Chdfs-dfs%E3%80%8D%E3%82%B7%E3%82%A7%E3%83%AB%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E9%81%95%E3%81%84%E3%81%AF%E4%BD%95%E3%81%A7%E3%81%99%E3%81%8B%EF%BC%9F/1040749564/
