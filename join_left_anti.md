# join_left_anti


- 左テーブルのみ残し、右テーブルの情報を除く
- 左テーブル＝右テーブルとなっている行は除く

```
val cusDF = spark.read.format("avro").load("/user/customers")

// 2014年3月の注文データを作る
val ordDF = spark.read.format("avro").load("/user/orders").
withColumn("order_date",to_date(from_unixtime($"order_date"/1000))).
filter("order_date LIKE '2014-03%'")

// 2014年3月の注文がない顧客を抽出(left_antiで2014年3月の注文をjoinしてそれを持ってる顧客を除外)
cusDF.join(ordDF,$"customer_id"===$"order_customer_id","left_anti").
select(cancat($"customer_fname", lit(":"),$"costomer_lname").as("name")).
write.mode("overwrite").json("/user/output")

```
