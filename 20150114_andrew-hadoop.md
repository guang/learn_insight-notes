1/14/2015 Wednesday
==========================
Whiteboard chat with Andrew about Hadoop (HDFS and MR) and Spark

## MapReduce is more than Map and Reduce
- *record reader*: parse data into records
- *map*: user-provided code executed on each key/value pair
- *combiner*: optional localized reducer that can group data in the map phrase
- *partitioner*: partitions and writes the results from map onto the HDFS
- *shuffle and sort*: reads the results on HDFS by downloading them to the local
  machine in which the reducer is running.
- *reduce*: takes grouped data as input and runs the reduce function once per key grouping
- *output format*: final key/value pair written out to file by a record writer. By default,
  key/value pairs are separated with a tab while records are separated by newline character.

Reference:  MapReduce Design Patterns by Donald Miner & Adam Shook, OReilly

## Hadoop
- Distributed data processing: MapReduce
- Distributed data storage: HDFS
  - Name Nodes: meta information, keeps track of hash map for each data node (master)
  - Data Nodes: where the blocks of file are physically stored.

## Hadoop MR vs Spark
- MapReduce and Spark both have to read through all data to process content (thus
  the time it would take for a non-repetitive task would be same for both)
- Both fire up JVM instances with allocated resources (for hadoop, it gets the information
  from namenode).
- (?) HDF

## Integrating Spark with Hadoop
- Spark can work standalone with HDFS
- Spark can also work with YARN on HDFS
