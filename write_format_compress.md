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

## t1q7
- write json
```
spark.read.format("parquet").load("/user/testdata/xxxfile").
withColumn("order_date",to_date(from_unixtime($"order_date"/1000))).
filter("order_date LIKE '2014-03%' and order_status='PENDING_PAYMENT'").
groupBy($"order_date").count.
write.mode("overwrite").format("json").save("/user/output")
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
