# タブ区切りファイルのload

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t2q1
- タブ区切りcsv

```
import org.apache.spark.sql.types._
val cusDF = spark.read.option("sep","\t").csv("/user/testdata/xxxfile").
select(col("_c0").as("cusid"),col("_c1").as("amount").cast(DoubleType))

```

## t2q1
- case class
- map関数

```
case class OrderItems(orderId:String,order_item_subtotal:Float)

val orderItemDF = spark.read.textFile("/user/testdata/xxxfile").map(x => x.split("\t")).map(i => OrderItems(i(1),i(4).toFloat))

```

## t2q3
- パイプライン(|)区切りcsv

```
val dataDF = spark.read.option("sep","|").csv("/user/testdata/xxxfile").select(col("_c0").as("fname"),col("_c1").as("city"))

```
