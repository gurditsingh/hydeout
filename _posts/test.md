### The return of RPC -  because REST is not only the solution for APIs

The REST API has been a pillar of web API's for a long time. But recently gRPC has started gaining popularity. It turns out there are some very good reasons for that. To help API developers make sense of which API design style to use and for what situation, let’s look at **REST** and **gRPC**.

**First Question come to our mind**

> How should I design my API ?  
> Which API sytle is best ? 
> What are the best patterns my particular API ?

**So this is a hard question to answer**

## if you pay attention to Twitter and conference talks a huge debate going on between RPC and Rest.

where a long time ago we used **RPC** but that not worked so we replace it with **REST** and then that not worked so we replaced it with **graph QL** and that's like the best thing  looking at API design. but I think it misses the point is not that the graph QL is the best thing for every situation or rest is the best thing for every situation the point is that these are actually different tools for different jobs.

## What is important ?

when you're designing an API instead of thinking about ton of different decisions all the time all these different design considerations. what you want to make important or what is important to you.

 - what isn't as important things like do you care about whether your API is tightly coupled.
 - what you want to make tight coupling you want some strong abstraction and very high-performance as they communicate and send messages to each other.

and it's totally fine for them to be very chatty on the wire on the network but other times you don't want that Chad miss you want very low network latency or very low network overhead
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzI2ODc4MTIzLC02NTQyMTE2MTAsNjQ1MT
E5ODgzLC04NTk1NDQ0MTksOTY1NjM3NDczLC0xMzgyMTE1MzQx
LDMwODczMDUzOSwtMTM0MjIzMjE4LDgxOTE1NTE4MCwtMTY4NT
k0NDUxMiw4NDE3MTg2MjIsNjE0NjAxNTg4LDE2OTU0NzU5MzEs
LTE2NjI2NDk4NzgsNDU4ODk0Mjc2LC0xODE2MDU3Njk3LC01Mz
IwMjM0MzgsLTMwOTEyMzA1Niw0NDMwNDQ1NjUsLTI1MjU5NzAx
Nl19
-->