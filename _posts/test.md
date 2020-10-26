

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

## **Let's do some Data Exploration (EDA) :**

 Let's create simple spark batch job to do some data exploration. We have Netflix sample data with Actors and TV Shows.
```scala
 def run(args: Array[String]): Unit = {

    val spark=SparkSession
      .builder()
      .master(args(0))
      .getOrCreate()

    val NFShow=loadNetflixTVShowData(spark)

    val NFActor=loadNetflixActorData(spark)

    println("Joining up the Actors and TV shows")
    NFShow.join(NFActor,NFActor.col("actor_id") === NFShow.col("actor_id"),"inner")
      .take(10)
      .foreach(println)

    println("Grouping TV shows genre and calculating the count")
    NFShow.groupBy(NFShow.col("genre"))
      .count()
      .take(10)
      .foreach(println)

  }
``` 

 **What happens in the spark when we kick off the exploration ?**
  
- Spark creates separate two jobs. One job for Joining the data and another for grouping the data. 
-   Spark runs the jobs serially.
  - Jobs are independent from each but spark runs in serially.

## Can spark run the above jobs at the same time ?
Spark can run multiple parallel jobs simultaneously. By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.
> Multiple parallel jobs can run simultaneously if they were submitted from
> separate threads. By “job”, in this section, we mean a Spark action
> (e.g. `save`, `collect`) and any tasks that need to run to evaluate
> that action.

## Parallel job submission:

To achieve concurrency at job level, we can leverage Scala concurrency features called [_Scala Futures_](https://docs.scala-lang.org/overviews/core/futures.html). Lets rework our above code using Scala futures to parallelize the job submission.
```scala
def run(args: Array[String]): Unit = {

    val spark=SparkSession
      .builder()
      .master(args(0))
      .getOrCreate()

    val NFShow=loadNetflixTVShowData(spark)

    val NFActor=loadNetflixActorData(spark)

    println("Joining up the Actors and TV shows")
    val joinFuture=Future {
      NFShow.join(NFActor, NFActor.col("actor_id") === NFShow.col("actor_id"), "inner")
        .take(10)
        .foreach(println)
    }
    println("Grouping TV shows genre and calculating the count")
    val groupFuture=Future {
      NFShow.groupBy(NFShow.col("genre"))
        .count()
        .take(10)
        .foreach(println)
    }

    Await.ready(joinFuture,Duration.Inf)
    Await.ready(groupFuture,Duration.Inf)

  }
```
 **What happens in the spark when we kick off the reworked exploration ?**
  
- Spark creates separate two jobs. One job for Joining the data and another for grouping the data. 
-   Spark runs the jobs parallel.
  - Jobs are independent from each other and spark runs in concurrently .
  

## Some scenario Scala futures would not help
Running concurrent jobs in spark application bring positive results and boost performance in most of the cases , however, there could be a scenario when alone Scala Futures would not help, it is because sometimes a job consumes all the resources and other jobs have to wait until they get some of it. In this case, we need to configure Spark’s FAIR scheduling which will ensure resources to all the triggered jobs.

```scala
 val spark=SparkSession
      .builder()
      .config("spark.scheduler.mode","")
      .config("spark.scheduler.allocation.file","scheduler.xml")
      .master("local")
      .getOrCreate()
```

 **Create a new Spark FAIR Scheduler pool :**
 There is more than one way to create FAIR pools. In this example, we will create a new file with the following content and save this file to the file system so we can reference it later.
```xml
<?xml version="1.0"?>

<allocations>
  <pool name="fair_pool">
    <schedulingMode>FAIR</schedulingMode>
    <weight>2</weight>
    <minShare>4</minShare>
  </pool>
  <pool name="a_different_pool">
    <schedulingMode>FIFO</schedulingMode>
    <weight>1</weight>
    <minShare>2</minShare>
  </pool>
</allocations>
```
The fair scheduler also supports grouping jobs into _pools_, and setting different scheduling options (e.g. weight) for each pool. This can be useful to create a “high-priority” pool for more important jobs,
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc2NTc4NjM2NSwyNTY2MjA4NDQsMTA5Nj
E1MjY5LC0zOTc3Mzc5MzUsMjAxNjkxMTE3MCwtMTMxMDQwMTkw
MCwxNjEwMTg3NzU1LC02MTg1NzY3MzUsLTE4MDU2MDkwNDcsLT
c0NzMwNDQwNSwtMTk2NTIwNjYzLC0yMDg4NzQ2NjEyLC0xMDMz
NTc3MTcwLDk1Mzc3MTk1OCwzNTA2NzkzMzEsNTg3NjE2NTcsMz
YyOTE1NzcxLDE0ODgzNDU4MjAsLTQ5MzMyMzYyNSwtMTI3ODQ2
Njc3XX0=
-->