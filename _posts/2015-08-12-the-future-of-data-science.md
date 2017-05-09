---
layout: post
title: The future of Map Reduce
tags: [analytics, bigdata, curation, database, dbms, hadoop, mapreduce, nlp]
comments: true
---

Whenever I read about **big data** analytics, names like *Hadoop* and *MapReduce*
pop out consistently. Specifically, the Hadoop framework allows to execute a
number of traditional algorithms on massive datasets, without having any
knowledge of systems engineering, load balancing, high performance computing
etc. 
This "new" programming paradigm goes under the name of **MapReduce**,
which consists of 

1) breaking up the dataset in pieces that can be handled independently 

2) mapping a function to each one of them and 

3) reducing the results into a unique record

That is exactly what Google invented about ten years ago, and what Yahoo implemented and 
then released as opensource project for the community. 
It turns out that five years ago, Google dropped the MapReduce paradigm for something 
that we do not know, yet. We will probably know the day they decide to abandon that other 
approach for something even better. 
What captured my attention is that today we consider MapReduce as the
ultimate solution to the big data analytics problem. Namely, a technology that
is quite obsolete for others. 
However, it seems to me that MapReduce is kind
of dead before its viral spreading. As a matter of fact the MapReduce
revolution is changing the architecture of several database systems, forcing
the community to switch to other paradigms, not always as efficient as
traditional ones. The guys working with social media are going towards the
adoption of graph databases. 

The adoption of JSON as an exchanging data format
for the web is leading towards *noSQL* databases, which deals with unstructured
data. Theories like *Entity Resolution* are getting more and more the attention
of data scientists whose ultimate goal is to make unstructured data,
structured. Many scientists are even abandoning the ACID paradigm of
traditional DBMS systems. This is happening with the adoption of Hadoop and
its HDFS file system even for database query engines. 
Anything wrong with that? Not really. 

No database system would like a file system that cannot
guarantee that the data is not on the current node but somewhere else in the
network. 

> Every DBMS wants ACID. 

Impala realised this simple fact, and
developed a Massively Parallel Processing query engine that runs on Hadoop but
does not use the MapReduce paradigm, which is very expensive.

**[Impala](http://www.cloudera.com/content/cloudera/en/products-and-services/cdh/impala.html)** 
runs separate Daemons which split the query and execute it in parallel, merging the results at the end of each operation. 
All of this occurs in memory, a bit like in the flavor of [Apache Spark](http://spark.apache.org/). 

Impala caches as much as possible from queries to results and supports columnar formats, which are much faster for
most of the queries that only hit a few columns. However, queries in Impala
are faster at the cost of a less fault tolerant process. Namely, a problem
during the query will make the query gone (which is what Hive on Hadoop would
not allow). 

Finally, data scientists are gradually moving from the _row-based_ approach to the _array-based_ one. 
Hence, DBMS systems that optimize performance in the latter architecture will make the difference in
the very near future.




