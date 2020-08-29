# write format

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q3


```
val dataFile = spark.read.parquet("/ssss/xxxfile").createOrReplaceTempView("product")

val xxx = spark.sql("select xxx from product")
```

## t2q7


```
import org.apache.spark.sql.types._

// dataframe作成
val proddf = spark.read.csv("/user/testdata/xxx/").
select(col("_c0").as("pId"),col("_c2").as("name"))

val orddf = spark.read.csv("/user/testdata/xxx/").
select(col("_c0").as("prodId"),col("_c4").as("order_total").cast(DoubleType))

// join
orddf.join(proddf,orddf("prodId")===proddf("pId")).createOrReplaceTempView("joined")
val filtDF = spark.sql("select concat("prodId,':',sum(order_total)) from joined group by prodId order by sum(order_total) desc limit 10")

filtDF.write.mode("overwrite").format("text").save("/user/output")

```
