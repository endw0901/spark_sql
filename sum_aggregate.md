# サマリ

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t2q1
- サマリ
- goupBy($"xxx").agg(sum($"xx"))

```
import org.apache.spark.sql.types._
val dataDF = spark.read.option("sep","\t").csv("/user/testdata/xxxfile").select(col("_c0").as("cusid"),col("_c1").as("amount").cast(DoubleType))

val sumDF = dataDF.select("cusid","amount").groupBy($"cusid").agg(sum($"amount") as "order_amount")

```
