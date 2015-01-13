1/13/2015 Tuesday
===========================
Introduction to projects


## General
you can actually build an existing service (ie google maps)

merging:
  - real-time and static
  - multiple sources

“engineer” (ie fake) data when there’s not much of it

focus more on building structure rather than analysis/getting insights

a good problem/project is
  - well defined, clear
  - involves trade-offs (ie CP vs AP)

## Two approaches to a good project
Remember the different components of the data pipeline

Ingestion:
  - Kafka
  - Amazon Kinesis
  - Flume
  - Fluentd
  - Sqoop

Batch Processing:
  - Hadoop (MR/Pig/Hive)
  - Giraph
  - Spark (GraphX)

Real-time (Streaming) Processing (Speed Layer):
  - Storm
  - Spark Streaming

Distributed Data Store (Serving Layer):
  - Cassandra
  - MongoDB
  - HBase

Front-end:
  - API
  - UI

## Breadth first
Covers all aspect of building the pipeline

## Depth first
Explore existing tools, build unique solution/tool, demo it works (comparing/testing), then
release/open source

## General project requirement
  - Github Documentation
  - Pushing Failure (figuring out components that fail when scaling up)
  - Ensure Fault-Tolerence (robustness)
  - Performance Metrics (how well it works)
  - Tech Comparison (tradeoffs)

## Schedule
All through-out: Company visits

Week 1
- Picking project/data engineering use cases
  - Lucian
  - Nathan Marz (Lambda Arch)
  - Chris Fregly (Spark)
  - Pato Echague (Cassandra/RelateIQ)
- Wednesday:
  - Hadoop (MapReduce) Developmental Setup / Github
- Thursday:
  - Spark DevS
- Friday:
  - Demo (~ 5mins)
    - BF: where is data coming from (realtime/static)(format)(engineered?);
          example queries & why difficult (specific questions);
          tentative pipeline (technologies)(tradeoffs);
          about me (transition to DE)(background)(picture)
    - DF: describe the problem / why you need solution;
          discuss existing tools;
          propose solution;
          about me


Week 2
- MVP (Minimum Viable Pipeline)

Week 3
- Optimizing, Refactoring, Tech Comparison

Week 4
- Finishing Touches (front-end, documentation) / Demo

Week 5-7
- Demoing/Interview Prep

Week >8
- Interviews
