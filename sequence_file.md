# Sequenceファイルの作成

https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

# Bt2q4
- dataframe.rdd.map
- saveAsSequenceFile
```
val datadf = spark.read.csv("/user/testdata/Bt1q2.txt")

datadf.rdd.map(args => (args(0).toString,args.mkString(","))).saveAsSequenceFile("/user/output/solution")
```
