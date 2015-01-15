1/13/2015 Tuesday
===========================
Alumni visit with Jean-Marc (relateIQ) and Arthur (Airbnb)

## XML sucks - use Thrift
XML is not fun to work with because when you try to process it sometimes it is so huge
(50mbs) you cannot read it line by line (as does by hadoop). Actually I am still kinda
iffy how this works, should probably follow up.

Actually so other nested type formats are also bad (ie jason) since they are not line
by line - instead a better way would be to first convert them into a nicer structure
(thats all on one line, even something like csv is fine) via something like Apache Thrift.

## Transforming not-hadoop-friendly data
There are services that do this
- Thrift
- Protobuf (Protocol Buffers)
- Avro

## Scheduling timed scripts
cron scheduler in unix

## Kafka
Kafka is pretty awesome and lets you choose block size to be pushed onto HDFS
