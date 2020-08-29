# write format

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q1

```
val dataFile = spark.read.format("avro").load("/user/testdata/aaaafile")
dataFile.select("aaa","aaaa").write.option("compression","gzip").parquet("/user/output")
```

