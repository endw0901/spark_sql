# group by や having

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test


## t1q2
- havingはgroupByの後の「where」

```
val dataFile = spark.read.format("csv").load("/user/testdata/xx").
select(col("_c2").as("xxx"),col("_c3").as("xxx")).
filter($"status"==="COMPLETE").
groupBy("customer_id").count.where("count > 4").
join(xxx,"customer_id").sort("count").
write.mode("overwrite").json("/user/output")

```
