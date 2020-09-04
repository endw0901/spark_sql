# join

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

- sparkのjoinは、単位は左テーブルのinner joinになるため注意

```
例
顧客(顧客id)
1
2
3

注文（注文id,顧客id)
10,1
11,1
12,1
13,3

// join結果、単位は顧客ユニークで、注文2の顧客はいないので除かれる
顧客.join(注文,"顧客id") 
結果：
1
3

```

## t1q2
- join 列名が同じとき

```
val dataFile = spark.read.format("csv").load("/user/testdata/xx").
select(col("_c2").as("xxx"),col("_c3").as("xxx")).
filter($"status"==="COMPLETE").
groupBy("customer_id").count.where("count > 4").
join(xxx,"customer_id").sort("count").
write.mode("overwrite").json("/user/output")

```

## t1q8
- join 列名が違う時

```
val result = groupDF.join(cus, $"order_customer_id" === $"customer_id").select($"customer_fname",$"customer_lname",$"count",$"customer_status")
```


## t2q7
- テーブル名＋列名それぞれ指定してjoin
```
import org.apache.spark.sql.types._

// dataframe作成
val proddf = spark.read.csv("/user/testdata/xxx/").
select(col("_c0").as("pId"),col("_c2").as("name"))

val orddf = spark.read.csv("/user/testdata/xxx/").
select(col("_c0").as("prodId"),col("_c4").as("order_total").cast(DoubleType))

// join
orddf.join(proddf,orddf("prodId")===proddf("pId")).createOrReplaceTempView("joined")
val filtDF = spark.sql("select concat("prodId,':',sum(order_total)) 
                        from joined group by prodId order by sum(order_total) desc limit 10")

filtDF.write.mode("overwrite").format("text").save("/user/output")

```
