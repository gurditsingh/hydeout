

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**











**It does not mean spark cannot run concurrent jobs**
By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.







> Multiple parallel jobs can run simultaneously if they were submitted from
> separate threads. By “job”, in this section, we mean a Spark action
> (e.g. `save`, `collect`) and any tasks that need to run to evaluate
> that action.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxODU3NjczNSwtMTgwNTYwOTA0NywtNz
Q3MzA0NDA1LC0xOTY1MjA2NjMsLTIwODg3NDY2MTIsLTEwMzM1
NzcxNzAsOTUzNzcxOTU4LDM1MDY3OTMzMSw1ODc2MTY1NywzNj
I5MTU3NzEsMTQ4ODM0NTgyMCwtNDkzMzIzNjI1LC0xMjc4NDY2
NzcsLTk5OTAzMDMyMiwtMTcwNjczMTk5Miw5MDc4OTc3MjIsLT
EzNDM1ODAwNzYsLTE4NzI3NTk2NTksNjc5MzMyMzY1LC00MDM5
Nzc0NjFdfQ==
-->