# write format

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q3


```
val dataFile = spark.read.parquet("/ssss/xxxfile").createOrReplaceTempView("product")

val xxx = spark.sql("select xxx from product")
```
