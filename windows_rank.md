# Windows関数、rank

https://www.udemy.com/course/complete-cca-175-hadoop-spark-developer-with-practice-test

## t2q4
- meta-store table("product_ranked")がある前提

- dense_rank() :件数は変わらない。ランクを付ける→次のフィルターで1位のみ残す
- https://www.oracle.com/jp/technical-resources/article/set-of-sql-of-the-oracle-database.html

```
val dataDF = spark.sql("select p.product_category_id, p.product_name, p.product_price,
　　dense_rank() over (partition by p.product_category_id order by p.product_price) as product_price_rank
  　from product_ranked p").
  
filter("product_price_rank=1").
map(x => x.mkString("|")
```
