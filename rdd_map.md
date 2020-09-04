# RDD MAP (KEY VALUE)

- no compression as sequencefile
- keyとvalueの指定があり
- valueはパイプ区切り

```
val datafile = spark.read.parquet("/user/input")

datafile.rdd.map(x => (x(0).toString,x.mkString("|"))).saveAsSequenceFile("/user/output")
```
