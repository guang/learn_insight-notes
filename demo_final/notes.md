Transcript of the Demo for Insight Project
=======================
Guang Yang


## Motivation (1:05)

Starcraft II is a real-time strategy game - basically you start with a base and you make
stuff and try to kill your enemy. There are a few things that keep the game interesting
as it evolves, the one that Im gonna look at is maps

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
unbalanced towards a certain playstyle. To do this, I mine a lot of player-submitted replay
data. In the end, I hope my tool would allow developers to decide on which maps to keep
or to throw away in the new season.

## Demo
One question a game developer might want to know is whether a map is overpowered for
early rushing. The direct metric for this is the duration of the game. If early rushing is
super good, we would expect the average match duration to be quite low comparing to
other maps. So for example, lets check out daybreak. What you see here is match duration
averaged by day. It is still very noisy, however as a data scientist, you can directly
query and get this data via my API to do further analyses.

## Pipeline (1:55)
Here is an overview of my technology stack. Coming out of Berkeley, as you can see im a big
spark fanboy. I will go into more details about each section in
the following slides.

### Ingestion
I get my data from a site called GGtracker that lets users submit their replay files to
be analyzed.
They have approximately 500gbs of JSON files. Their API has a 1 second
limit so to mine the data more effectively I used my EC2 nodes to mine in parallel via tmux.
I then serialize the data via avro then publish to kafka.

I think serialization in general is good practice for that it enforces schema, is
splittable on HDFS, backward compatible if you change your schema, and it saves space.
On the left is a raw json file from the API call, and on the right is what it looks like
after serialization. Notice it becomes just one line in the avro file and the schema is
encoded at the top. Out of
thrift and protobuf, I liked avro the best because all my data come in as JSON. 


### Batch
After getting my data onto HDFS, I use Spark SQL to directly read the avro files into
schemaRDDs, which behave like regular RDDs, and do computations and generate batch views.
Thanks to a datastax connecter, I am able to directly push my batch views from Spark
into tables in Cassandra. In turn my front-end API queries directly against the tables in
Cassandra.

For streaming I am hitting the GGtracker API every second to get a list of the most recent
replays to feed into spark streaming to get the most recent maps played.

I chose Spark because I thought in-memory computation is pretty cool and fits well
with my problem as I am generating different views from the same data. Spark SQL in
particular because of abstraction and the ease to directly load avro files.

I chose an AP data-store because in my use case availability is prefered over consistency
for it is better to show graphs with outdated data rather than no graph at all.
I liked Cassandra in particular because I thought the tunable consistency seems like a
pretty cool solution to AP vs CP.




## About me (0:07)
My name is Guang. I did my undergrad in Applied Math and just finished my master in O.R. at
Berkeley. Here is me taking an echocardiogram at Texas Childrens Hospital to get some imaging
data for senior design project. It was not ultra sound. Thank you for your time.
