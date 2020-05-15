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
It is an adaptation of traditional RPC frameworks. gRPC is built on the core principle that we must use Services not Objects, and Messages not References. In other words, in gRPC we start the process by defining our services and their message types. We use clear interfaces that maps directly to our business functions and programming concept like interfaces or methods. No need for translations. gRPC is all about APIs, not resources.

## gRPC Strengths
The technology used to provide an API for your app is an important choice, and gRPC offers unique benefits compared to HTTP APIs.

### Performance:

 - gRPC is a binary protocol rather than text-based messaging protocol, it uses protocol buffers **(Protobuf serializes very quickly on the server and client)** as the binary data interchange format for inter-service communication.
 
 - gRPC is designed for HTTP/2, a major revision of HTTP that provides significant performance benefits over HTTP 1.x. HTTP/2 protocol provides Binary framing and compression and Multiplexing of multiple HTTP/2 calls over a single TCP connection

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ1OTk0NjczOCwxMzE2MzU0MTU2LDIwOT
I2NjE1NTksLTcxMDUyODcwLC03MTA1Mjg3MCwtMTc0NjI1ODMx
MywtMTAzNDM1NjUxNywxNDI4OTk3NzI4LC02NTQyMTE2MTAsNj
Q1MTE5ODgzLC04NTk1NDQ0MTksOTY1NjM3NDczLC0xMzgyMTE1
MzQxLDMwODczMDUzOSwtMTM0MjIzMjE4LC0yMTA2OTg0NjI1LC
0zMzI0NTUzNjNdfQ==
-->