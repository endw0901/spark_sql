# 文字列操作：substring

https://www.udemy.com/course/cca-175-spark-and-hadoop-developer-practice-tests-a

# Bt3q1
- yyyy-mm-ddをyyyy-mmに変換
- as order_dateとする必要なし(as不要)

```
val datadf = spark.read.option("inferSchema",true).csv("/uers/xxx").toDF("xx","xx")

datadf.createOrReplaceTempView("orders")

val result = spark.sql("""

SELECT Substring(order_date,1,7) order date,order_status,Count(1) cnt
from orders
where order_status = 'SUSPECTED_FRAUD'
GROUP BY Substring(order_date,1,7),order_status
ORDER BY order_date desc
""").select("order_date","cnt")

result.repartition(1).write.option("compression","snappy").parquet("/user/output")

```

### coalesceとrepartitionの違い

- https://www.it-swarm.dev/ja/apache-spark/%E3%82%B9%E3%83%91%E3%83%BC%E3%82%AF-repartition%EF%BC%88%EF%BC%89%E3%81%A8coalesce%EF%BC%88%EF%BC%89/1054280275/
- coalesceは、シャッフルされるデータ量を最小限に抑えるために既存のパーティションを使用します。 repartitionは新しいパーティションを作成し、フルシャッフルを行います。 coalesceは異なる量のデータを持つパーティション（時にはサイズがかなり違うパーティション）になり、repartitionはほぼ同じサイズのパーティションになります。
