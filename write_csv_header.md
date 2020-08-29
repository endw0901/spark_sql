# ヘッダ付きCSVファイル出力

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t2q1

- schemaがある前提

```
dataDF.write.mode("overwrite").option("header","true").csv("/user/output")
```


