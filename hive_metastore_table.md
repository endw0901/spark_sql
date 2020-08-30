# hive metastore テーブル

https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

# Bt2q1
- partitionのコンフィグ設定
- partitionBy + format("hive") + saveAsTable
```
case class customer(ordid:String,depid:String,name:String)
val datadf = spark.read.csv("/user/testdata/Bt1q2.txt").map(i => customer(i(0).toString,i(1).toString,i(2).toString))

spark.sqlContext.setConf("hive.exec.dynamic.partition","true")
spark.sqlContext.setConf("hive.exec.dynamic.partition.mode","nonstrict")

datadf.write.partitionBy("name").format("hive").saveAsTable("default.category_partitioned")

```

# Bt2q3
- 事前にtable作成してからsaveAsTable
- parquet形式

```
val datadf = spark.read.option("inferSchema",true).csv("/user/testdata/Bt1q2.txt").toDF("pid","depid","name")

spark.sql("""
CREATE TABLE IF NOT EXISTS default.categories
(
category_id INT,
category_name STRING
)
stored AS parquet
""")

datadf.select("pid","name").write.mode("overwrite").saveAsTable("default.categories")
```


# Bt2q6
- metastore tableからread・・・普通にspark sqlのfromでdefault.xxxxで読むだけ（データベース：default、テーブル：xxx)

