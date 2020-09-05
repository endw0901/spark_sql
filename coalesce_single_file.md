## シングルファイルにまとめたいとき

- file should be sotored in a single file => coalesce(1)
 
```scala:
val productDF = spark.read.parquet("/user/parquetfile").createOrReplaceTempView("product")

val maxDF = spark.sql("select concat(product_category_id,'|',max(product_price) from groduct group by product_category_id order by max(product_price) desc")

maxDF.coalesce(1).write.mode("overwrite").option("compression","gzip").format("text").save("/user/output")
```
