# 日付形式のフォーマット変換

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q7
- UNIXタイムを日時変換

```
spark.read.format("parquet").load("/user/testdata/xxxfile").
withColumn("order_date",to_date(from_unixtime($"order_date"/1000))).
filter("order_date LIKE '2014-03%' and order_status='PENDING_PAYMENT'").
groupBy($"order_date").count.
write.mode("overwrite").format("json").save("/user/output")
```

https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

## t1q1

```
val data = spark.read.parquet("/user/testdata/xxxfile")
val result = data.filter($"order_status" === "COMPLETE").select($"order_id",$"order_date", $"order_status").
              withColumn("order_date",to_date(from_unixtime($"order_date"/1000)))
result.write.option("compression","gzip").json("/user/output")
```
