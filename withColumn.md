# 文字列操作、新規列追加、列定義置き換え

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test


## t1q5

- 新規列名なら列追加、同名なら列定義を置き換え

https://x1.inkenkun.com/archives/1202

- substring(aaa,1,2)で1～2桁目のはず？

```
// 
cusDF.withColumn("fname",substring(col("fname"),0,3)).map(x => x.mkString("\t")).
write.mode.option("compression","bzip2").format("text").save("/user/output")

```
