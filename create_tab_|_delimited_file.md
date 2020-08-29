# タブ区切り、| 区切りファイル(dataframe)の作成

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test


## t1q3

- sparksql

```
val dataFile = spark.read.parquet("/ssss/xxxfile").createOrReplaceTempView("product")

val dataDF = spark.sql("select concat(category, '|', max(price)) from product groupby category order by max(price) desc")
```


## t1q5

- map関数

```
cusDF.withColumn(xxxxxx).map(x => x.mkString("\t")).
write.mode.option("compression","bzip2").format("text").save("/user/output")

```
