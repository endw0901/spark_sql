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
