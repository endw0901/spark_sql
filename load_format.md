# load format

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q1

- avro

```
val dataFile = spark.read.format("avro").load("/user/testdata/aaaafile")
```



## t1q3

- parquet

```
val dataFile = spark.read.parquet("/user/testdata/aaaafile").createOrReplaceTempView("product")
```

