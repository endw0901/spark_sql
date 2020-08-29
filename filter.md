# filter

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q7
- LIKE
- 複数条件(AND)
```
spark.read.format("parquet").load("/user/testdata/xxxfile").
withColumn("order_date",to_date(from_unixtime($"order_date"/1000))).
filter("order_date LIKE '2014-03%' and order_status='PENDING_PAYMENT'").
groupBy($"order_date").count.
write.mode("overwrite").format("json").save("/user/output")
```
