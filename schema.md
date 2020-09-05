# スキーマ

- 他＝＞case class参照

## inferSchema

- スキーマ推測(inferSchema)からtoDFでdataframe作成⇒view

```
val datadf = spark.read.option("inferSchema",true).option("delimiter","\t").csv("/user/testdata/Bt1q4.txt").toDF("fname","lname","state")
datadf.createOrReplaceTempView("view1")

val result = spark.sql("""
SELECT Concat_ws(' ', fname, lname) name from view1 where state = 'CA'
""")

result.write.text("/user/output")

```

## スキーマ作成

```
val schema = Seq("cusid","name","city")
var cusdf = spark.read.option("sep","\t").csv("/user/inputfile").toDF(
```
