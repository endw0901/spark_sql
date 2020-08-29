# タブ区切り、| 区切りファイル(dataframe)の作成

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test


## t1q3
- sparksql
```
val dataFile = spark.read.parquet("/ssss/xxxfile").createOrReplaceTempView("product")

val dataDF = spark.sql("select concat(category, '|', max(price)) from product groupby category order by max(price) desc")
```


## t1q5
- map関数:mkString
- タブ区切り
```
cusDF.withColumn(xxxxxx).map(x => x.mkString("\t")).
write.mode.option("compression","bzip2").format("text").save("/user/output")
```

## t2q4
- map関数:mkString
- パイプ区切り
- meta-store table("product_ranked")がある前提
```
val dataDF = spark.sql("select p.product_category_id, p.product_name, p.product_price, dense_rank() over (partition by p.product_category_id order by p.product_price) as product_price_rank from product_ranked p").
filter("product_price_rank=1").
map(x => x.mkString("|")
```


https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

## t1q4

- 名 + 空白 + 姓  ※空白を区切り文字として文字列を連結

```
val datadf = spark.read.option("inferSchema",true).option("delimiter","\t").csv("/user/testdata/Bt1q4.txt").toDF("fname","lname","state")
datadf.createOrReplaceTempView("view1")

val result = spark.sql("""
SELECT Concat_ws(' ', fname, lname) name from view1 where state = 'CA'
""")

result.write.text("/user/output")

```
