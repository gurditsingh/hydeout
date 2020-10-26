

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

**Let's do some Data Exploration (EDA) :** Let's create simple spark batch job to do some data exploration. We have Netflix sample data with Actors and TV Shows.
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

## What happens in the spark when we kick off the exploration ?









**It does not mean spark cannot run concurrent jobs**
By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.







> Multiple parallel jobs can run simultaneously if they were submitted from
> separate threads. By “job”, in this section, we mean a Spark action
> (e.g. `save`, `collect`) and any tasks that need to run to evaluate
> that action.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0ODM5MjkyNiwyMDE2OTExMTcwLC0xMz
EwNDAxOTAwLDE2MTAxODc3NTUsLTYxODU3NjczNSwtMTgwNTYw
OTA0NywtNzQ3MzA0NDA1LC0xOTY1MjA2NjMsLTIwODg3NDY2MT
IsLTEwMzM1NzcxNzAsOTUzNzcxOTU4LDM1MDY3OTMzMSw1ODc2
MTY1NywzNjI5MTU3NzEsMTQ4ODM0NTgyMCwtNDkzMzIzNjI1LC
0xMjc4NDY2NzcsLTk5OTAzMDMyMiwtMTcwNjczMTk5Miw5MDc4
OTc3MjJdfQ==
-->