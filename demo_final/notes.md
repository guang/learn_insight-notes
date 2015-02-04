Transcript of the Demo for Insight Project
=======================
Guang Yang


## Motivation (1:05)

Starcraft II is a real-time strategy game - so basically you start with a base and you make
stuff and try to kill your enemy. There are a few factors that keep the game interesting
as it evolves, the one that I wanna look at is maps

Let me show you why maps change how you play the game. Here is a regular map, [PAUSE] here are
the two bases [PAUSE], most units are ground units so to get to your enemys
base you need to travel a long distance.

Here is a more interesting map. [PAUSE] Two bases [PAUSE] still long way to go by foot
[PAUSE] but now the proximity allows for more potent air harassment and early rushes

For both developers and players, game balance is super important - and in terms of maps, this
is really tricky because on one hand you want to encourage players to come up with new
tactics based around new maps, but at the same time you dont want any particular playstyle
to be overpowered.

I thought it would be cool to use data to track how each map is doing - whether they are
unbalanced towards a certain playstyle. By looking through vast amount of replays
submitted by players, I hope my tool would allow developers to decide on which maps to keep
or to throw away in the new season.

## Demo

## Pipeline (1:55) (no streaming)
Here is an overview of my technology stack. Coming out of Berkeley, as you can see im a big
spark fanboy. I will go into more details about each section in
the following slides.

### Ingestion
I get my data from a site called GGtracker that lets users submit their replay files to
be analyzed.
They currently have 5 million replays from the past few years. Each replay is about 100kb
in size, so the whole thing is about 500gbs. Their API has a 1 second
limit so to mine the data more effectively I used my EC2 nodes to mine in parallel via tmux.
I then serialize the data via avro then publish to kafka.

I think serialization in general is good practice for that it enforces schema, is
splittable on HDFS, backward compatible if you change your schema, and it saves space. Out of
thrift and protobuf, I liked avro the best because all my data come in as JSON. Here is
before and after the serialization. Notice the schema is embeded into the avro file.


### Batch
After getting my data onto HDFS, I use Spark SQL to directly read the avro files into
schemaRDDs, which behave like regular RDDs, and do computations and generate batch views.
Thanks to a datastax connecter, I am able to directly push my batch views from Spark
into tables in Cassandra. In turn my front-end API queries directly against the tables in
Cassandra.

I chose Spark because I thought in-memory computation is pretty cool and fits well
with my problem as I am generating different views from the same data. Spark SQL in
particular because of abstraction and the ease to directly load avro files.

I chose an AP data-store because in my use case availability is prefered over consistency
for it is better to show graphs with outdated data rather than no graph at all.
I liked Cassandra in particular because I thought the tunable consistency seems like a
pretty cool solution to AP vs CP.

### Streaming




## About me (0:07)
My name is Guang. I did my undergrad in Applied Math and just finished my master in O.R. at
Berkeley. Thank you for your time.
