# filter

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test


## t1q2
- $の要否？
https://stackoverflow.com/questions/40223901/how-does-symbol-working-when-selecting-columns-from-dataframe
- 文字列Stringを列column名称として認識するということ

```
// $ : It comes from StringToColumn implicit inner class in SQLImplicits (which is implemented by the implicits object).

val dataFile = spark.read.format("csv").load("/user/testdata/xx").
select(col("_c2").as("xxx"),col("_c3").as("xxx")).
filter($"status"==="COMPLETE").
groupBy("customer_id").count.where("count > 4").
join(xxx,"customer_id").sort("count").
write.mode("overwrite").json("/user/output")

```

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
