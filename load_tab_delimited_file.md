# タブ区切りファイルのload

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t2q1
- タブ区切りcsv

```
import org.apache.spark.sql.types._
val cusDF = spark.read.option("sep","\t").csv("/user/testdata/xxxfile").select(col("_c0").as("cusid"),col("_c1").as("amount").cast(DoubleType))

```
