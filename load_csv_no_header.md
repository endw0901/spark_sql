# ヘッダ無しCSV

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t1q2

```
val dataFile = spark.read.format("csv").load("/user/testdata/xx").
select(col("_c2").as("xxx"),col("_c3").as("xxx")).
filter($"status"==="COMPLETE").
groupBy("customer_id").count.where("count > 4").
join(xxx,"customer_id").sort("count").
write.mode("overwrite").json("/user/output")

```


## t2q7
- case classを使用
- textファイルとしてタブ区切りで読み取り
```
case class Products(pId:Integer,name:String)
case class Orders(prodId:Integer,order_total:Float)

val prodDF = spark.read.textFile("/user/testdata/xxxx/").map(x => x.split(",")).map(c => Products(c(0).toInt,c(2)))
val ordDF  = spark.read.textFile("/user/testdata/xxxx/").map(x => x.split(",")).map(c => Orders(o(0).toInt,o(4).toFloat))

ordDF.join(prodDF,ordDF("prodId")===prodDF("pId")).createOrReplaceTempView("joined")
val filtDF = spark.sql("select concat(prodId,'|',sum(order_total)) 
             from joined group by prodId order by sum(order_total) desc limit 10")

filtDF.write.mode("overwrite").format("text").save("/user/output")

```


https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a


## t1q6
- inferSchemaでdataframe作成
- カンマ区切りtextファイル = csvで読める

```
val datadf = spark.read.option("inferSchema",true).csv("/user/testdata/Bt1q2.txt").toDF("pid","catId","name")

val datadf2 = datadf.map(x => x.mkString("\t"))
datadf2.write.mode("overwrite").option("compression","lz4").text("/user/output")

```
