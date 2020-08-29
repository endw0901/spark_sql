# hiveテーブルに出力

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q8


```
spark.sqlContext.sqlConf("hive.exec.dynamic.partition","true")
spark.sqlContext.sqlConf("hive.exec.dynamic.partition.mode","nonstrict")

result.write.partitionBy("customer_state").format("hive").saveAsTable("customer_order")
```
