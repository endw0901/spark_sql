# Sequenceファイルの作成

https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

# Bt2q4
- dataframe.rdd.map
- saveAsSequenceFile
```
val datadf = spark.read.csv("/user/testdata/Bt1q2.txt")

datadf.rdd.map(args => (args(0).toString,args.mkString(","))).saveAsSequenceFile("/user/output/solution")
```

# Bt2q5
- sequencefileの読み込み

- https://www.it-swarm.dev/ja/hadoop/hdfs%E3%81%8B%E3%82%89%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E3%81%AB%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E3%82%B3%E3%83%94%E3%83%BC%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95/1041036095/

```
// hdfsからVMローカルにGET
hadoop fs -get /user/outoput
```
