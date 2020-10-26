

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

**Let's do some Data Exploration (EDA) :**











**It does not mean spark cannot run concurrent jobs**
By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.







> Multiple parallel jobs can run simultaneously if they were submitted from
> separate threads. By “job”, in this section, we mean a Spark action
> (e.g. `save`, `collect`) and any tasks that need to run to evaluate
> that action.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYxMDE4Nzc1NSwtNjE4NTc2NzM1LC0xOD
A1NjA5MDQ3LC03NDczMDQ0MDUsLTE5NjUyMDY2MywtMjA4ODc0
NjYxMiwtMTAzMzU3NzE3MCw5NTM3NzE5NTgsMzUwNjc5MzMxLD
U4NzYxNjU3LDM2MjkxNTc3MSwxNDg4MzQ1ODIwLC00OTMzMjM2
MjUsLTEyNzg0NjY3NywtOTk5MDMwMzIyLC0xNzA2NzMxOTkyLD
kwNzg5NzcyMiwtMTM0MzU4MDA3NiwtMTg3Mjc1OTY1OSw2Nzkz
MzIzNjVdfQ==
-->