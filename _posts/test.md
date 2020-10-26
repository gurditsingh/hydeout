

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

**Let's do some Data Exploration (EDA) :** Let's create simple spark batch job to do some data exploration. We have Netflix sample data with Actors and TV Shows.
 










**It does not mean spark cannot run concurrent jobs**
By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.







> Multiple parallel jobs can run simultaneously if they were submitted from
> separate threads. By “job”, in this section, we mean a Spark action
> (e.g. `save`, `collect`) and any tasks that need to run to evaluate
> that action.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNjkxMTE3MCwtMTMxMDQwMTkwMCwxNj
EwMTg3NzU1LC02MTg1NzY3MzUsLTE4MDU2MDkwNDcsLTc0NzMw
NDQwNSwtMTk2NTIwNjYzLC0yMDg4NzQ2NjEyLC0xMDMzNTc3MT
cwLDk1Mzc3MTk1OCwzNTA2NzkzMzEsNTg3NjE2NTcsMzYyOTE1
NzcxLDE0ODgzNDU4MjAsLTQ5MzMyMzYyNSwtMTI3ODQ2Njc3LC
05OTkwMzAzMjIsLTE3MDY3MzE5OTIsOTA3ODk3NzIyLC0xMzQz
NTgwMDc2XX0=
-->