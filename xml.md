# xmlファイル

```
spark.read.csv("/user/input/xml").
select(substring(col("_c0"),0,3).as("fname"),substring(col("_c1"),0,2).as("lname")).
select(concat(col("fname"),lit(":"),col("lname")).as("fullname")).
write.format("com.databricks.spark.xml").
option("rootTag","persons").option("rowTag","persons").save("/user/output/xml")
```
