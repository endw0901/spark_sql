# join

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test


## t1q2
- join 列名が同じとき

```
val dataFile = spark.read.format("csv").load("/user/testdata/xx").
select(col("_c2").as("xxx"),col("_c3").as("xxx")).
filter($"status"==="COMPLETE").
groupBy("customer_id").count.where("count > 4").
join(xxx,"customer_id").sort("count").
write.mode("overwrite").json("/user/output")

```

## t1q8
- join 列名が違う時

```
val result = groupDF.join(cus, $"order_customer_id" === $"customer_id").select($"customer_fname",$"customer_lname",$"count",$"customer_status")
```