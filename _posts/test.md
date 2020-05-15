### The return of RPC -  because REST is not only the solution for APIs

The REST API has been a pillar of web API's for a long time. But recently gRPC has started gaining popularity. It turns out there are some very good reasons for that. To help API developers make sense of which API design style to use and for what situation, let’s look at **REST** and **gRPC**.

**First Question come to our mind**

> How should I design my API ?  
> Which API sytle is best ?
> What are the best patterns my particular API ?

**So this is a hard question to answer**

## if you pay attention to Twitter and conference talks a huge debate going on between RPC and Rest.

where a long time ago we used **RPC** but that not worked so we replace it with **REST** and then that not worked so we replaced it with **graph QL** and that's like the best thing  looking at API design. but I think it misses the point is not that the graph QL is the best thing for every situation or rest is the best thing for every situation the point is that these are actually different tools for different jobs.

## Design Considerations ?

When you're designing an API you have to think about ton of different decisions all the time all these different design considerations about what you want to make important or what is important to you and what isn't as important.

 - Coupling
 - Chattiness
 - Client Complexity
 - Cognitive Complexity
 - Caching
 - Discoverability
 - Versioning

> API designers or API builders is understand all of the trade-offs that go into various styles of API design that way we can pick the style that's going to fit best for a project.

# RPC Architecture
RPC stands for Remote Procedure Call. As the name suggests, the idea is that we can invoke a function/method on a remote server. RPC protocol allows one to get the result for a problem in the same format regardless of where it is executed. It can be local or in a remote server using better resources.

RPC is a much older protocol than REST. It has been used since  1970s to perform network operations. The idea is the same. An API is built by defining public methods. Then the methods are called with arguments. RPC is just a bunch of functions. Traditionally, RPC can be implemented as RPC-XML and RPC-JSON.

> **gRPC** is the latest framework to be created on the RPC protocol. It makes use of its advantages and tries to correct the issues of traditional RPC.

# What Is gRPC ?
It is an adaptation of traditional RPC frameworks. 

Rather, using a text-based messaging protocol, we can leverage a binary protocol that is optimized for inter-service communication. The Cloud Native Computing Foundation’s [gRPC](https://grpc.io/) (gRPC Remote Procedure Call) is an ideal choice for inter-service communication since it uses protocol buffers as the binary data interchange format for inter-service communication.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMxNjM1NDE1NiwyMDkyNjYxNTU5LC03MT
A1Mjg3MCwtNzEwNTI4NzAsLTE3NDYyNTgzMTMsLTEwMzQzNTY1
MTcsMTQyODk5NzcyOCwtNjU0MjExNjEwLDY0NTExOTg4MywtOD
U5NTQ0NDE5LDk2NTYzNzQ3MywtMTM4MjExNTM0MSwzMDg3MzA1
MzksLTEzNDIyMzIxOCwtMjEwNjk4NDYyNSwtMzMyNDU1MzYzXX
0=
-->