1/19/2015 Monday
==============================
Hadoop Chat with Sujee Maniyam

## Cloudera vs Horton Works
in terms of SQL, CDH has Impala while HW has Tez

## EMR vs Hadoop
EMR might be a good choice for making only batch jobs whereas a 24/7 Hadoop cluster is needed
to support things like HBase that makes queries on demand.

## Backing shit up on S3
Name Node is single point of failure, keep a backup of (raw) data on S3

## Does not need HDFS for Spark
Just use S3


## Use simple format up front, worry about parsing nested formats (ie JSON, XML) later
dont waste time trying to make it work with harder format first

## Spark vs Pig
Spark works much better on medium/small scale, pig can be more succint when working on
more complex operations on bigger scales

## Hive vs Pig
Hive is better for quering while Pig is better at massaging and transforming data

## Get Mo Practice
https://github.com/elephantscale/HI-labs

## Structures of Different NoSQL stores:
key/value vs column vs document vs graph

Hbase is column-based, dynamic regarding to columns (generate new column on the fly without
having to change schema)

aggregates on columns are much faster


## HBase vs HDFS
HDFS bad for small files (block size), HBase bad for big files ()

## Streaming Transformation
Webindexing: from
- mobile.cnn.com/news.html to com.cnn.mobile/news.html
- www.cnn.com/news.html to com.cnn.www/news.html

## performance vs integrity
- indexing for fast queries makes you vulnerable as you need to make multiple write updates
