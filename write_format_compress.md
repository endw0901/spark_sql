# write format

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q1

- write parquet

```
val dataFile = spark.read.format("avro").load("/user/testdata/aaaafile")
dataFile.select("aaa","aaaa").write.option("compression","gzip").parquet("/user/output")
```

## t1q6

- write parquet

```
.option("compression","uncompressed").parquet(xxxxx
```

## t1q2

- write json

```
xxx.write.json("/user/output")
```


## t1q3

- write text

```
datadf.write.mode("overwrite").option("compression","gzip").format("text").save("/user/output")
```


## t1q4

- write avro

```
cusdf.filter("city='Tokyo'").write.option("compression","deflate").format("avro").save("/user/output")
```
