# hiveテーブルに出力

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q8


```
spark.sqlContext.sqlConf("hive.exec.dynamic.partition","true")
spark.sqlContext.sqlConf("hive.exec.dynamic.partition.mode","nonstrict")

result.write.partitionBy("customer_state").format("hive").saveAsTable("customer_order")
```

## parquet形式のファイルをhive格納
```
spark.read.option("sep","|"),csv("/user/xxx/xxfile").
select(col("_c1").as("fname"),col("_c2").as("state").
where("fname like 'M%'").
groupBy("state").count.
write.mode("overwrite").option("compression","gzip").
option("fileformat","parquet").format("hive").saveAsTable("costomer_m")
```
