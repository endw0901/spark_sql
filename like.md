# like

https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

## t1q8

- スキーマ推測(inferSchema)からtoDFでdataframe作成⇒filter

```
val datadf = spark.read.option("inferSchema",true).csv("/user/testdata/Bt1q8.txt").toDF("id","price","name")

val datadf2 = datadf.filter($"price" > 1000.0).filter($"name".like("%TAK%"))
datadf2.write.mode("overwrite").option("compression","snappy").parquet("/user/output")

```
