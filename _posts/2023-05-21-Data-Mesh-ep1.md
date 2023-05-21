---
title: "Episode-1 'Data Mesh' : Evolution of data platforms"
layout: post
excerpt: "This post details the evolution of data platforms, highlights their problems, and why we decided to build a Data Mesh."
last_modified_at: 2023-05-21T11:02:01-05:00
tags:
  - Data Lakes
  - Data Warehouse
  - Data Platforms
  - Data Mesh
  - Data Architecture
  - Centralized Data
  - Monolithic
  - Decomposition
---

  
## The evolution of data platforms

Data platforms have evolved over time to meet the needs of businesses. In the early days, data platforms were centralized and focused on providing a single view of the truth for the enterprise. This was a valuable approach, but it had some limitations. Centralized data platforms can be expensive to build and maintain, and they can be slow to adapt to changes in the business environment.

In recent years, there has been a move towards decentralized data platforms. Decentralized data platforms are built around the idea of data ownership and control. Each team or business unit owns its own data, and it is responsible for managing and governing that data. This approach has a number of advantages. It is more agile and adaptable, and it can be more cost-effective.

> Before diving in the details of the decentralized data platform, let’s review how the information industry came to this situation.

## Data Management Architecture
Data management architecture is a critical component of any organization's data strategy. It defines how data is collected, stored, managed, and used throughout the organization. A good data management architecture can help organizations to:

-   Improve data quality
-   Increase data security
-   Reduce data redundancy
-   Improve data access and usability
-   Make better decisions based on data

A bad data management architecture can lead to a number of problems, including:

-   Inconsistent data
-   Data silos
-   Data quality problems
-   Data security breaches
-   Poor decision-making

It is important for organisations to have a well-defined data management architecture in place. Most organisations prefer to start with a central data team and a monolithic data management architecture where all data operations are carried out from and to a single, centralized data platform.


> A centralized data team and a monolithic data management architecture are the most common approach to data management. This approach is easy to set up and can handle small-scale data analytics and storage without performance degradation. However, as data volume and demand increase, this approach can become a bottleneck.


## Generation's of data platform
It's not uncommon for organisations to learn from the failures or limitations of previous data and analytics platforms and embark on building new and improved generations.

**The first generation** of data and analytics platforms were designed for a time when data was scarce and expensive. These platforms were typically centralized and focused on data warehousing and reporting. ETL jobs, tables and reports that only a small group of specialized people.

**The second generation** of data and analytics platforms was big data and data lake. This generation of platforms was designed to address the limitations of the first generation, which was focused on data warehousing and reporting. Big data platforms are designed to store and analyze large volumes of data, while data lakes are designed to store all types of data, both structured and unstructured.

**The third generation** of data and analytics platforms are designed to address the limitations of the first two generations. These platforms are typically cloud-based, scalable, and integrated with other systems. They also offer a wider range of capabilities, such as machine learning and artificial intelligence.

## Architectural failure of different generations
All generations of data platforms carry a number of architectural failure modes and limitations. Some of the most common include:

#### 1. Centralized and monolithic
While over the last decade we have successfully applied domain driven design and bounded context to our operational systems, we have largely disregarded the domain concepts in a data platform. We have moved away from domain oriented data ownership to a centralized domain agnostic data ownership.

![monolithic](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/data_mesh_1.jpg?raw=true)


Domain-driven design is a software development approach that focuses on the domain of the problem being solved. By understanding the domain, developers can create software that is more intuitive and easier to use. Bounded context is a technique used in domain-driven design to divide the domain into smaller, manageable pieces. This can help to improve the scalability and maintainability of the software.

Data ownership is the responsibility for managing and governing a specific data set. In a domain-oriented data ownership model, each domain owns its own data. This can help to ensure that data is used in a consistent and accurate manner. It can also help to improve the security and privacy of data.

A centralized domain agnostic data ownership model means that a single team or department is responsible for managing and governing all of the data in the organization. This can make it difficult to ensure that data is used in a consistent and accurate manner. It can also make it more difficult to improve the security and privacy of data.


A monolithic data architecture is a framework where application data is stored, into centralized data store and it evolve several challenges.
  

 1. The monolithic data architectures are not scalable and can become slow and expensive as the volume of data increases. This is because monolithic databases are designed to store all of an organisations data in a single location. As the volume of data increases, the load on the database increases, which can lead to performance degradation. Additionally, monolithic databases are often expensive to implement and maintain.
 2. Monolithic data architectures are tightly coupled, which means that changes to one part of the architecture can impact other parts of the architecture. This can make it difficult to make changes to the architecture and can lead to architectural failure.
 3. The monolithic data architectures, concurrent reads and writes from different teams and methods within an application can result in high latency and reduced throughput.

> While this centralized model can work for organizations that have a simpler domain with smaller number of diverse consumption cases, it fails for enterprises with rich domains, a large number of sources and a diverse set of consumers.

#### 2. Decomposition of coupled pipeline
The decomposition of a centralized data platform into these mechanical functions (ingestion, cleansing, aggregation, serving, etc.) can help to improve the efficiency and effectiveness of the platform. By focusing on each function individually, it is possible to optimize the process of collecting, storing, and managing data.

Data platform architectures have evolved over time, and the current generation of architectures are based on the idea of decomposing the platform into a pipeline of data processing stages.

![pipeline](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/data_mesh_2.jpg?raw=true)

The decomposition model has a number of benefits, but it also has some limitations. One of the limitations is that it can slow the delivery of features. This is because each stage of the pipeline is responsible for a specific task, and there can be a lot of communication and coordination between the different stages. This can lead to delays in the overall delivery of the feature.

Another limitation of the decomposition model is that it can lead to high coupling between the stages of the pipeline. This means that changes to one stage can have a ripple effect on other stages. This can make it difficult to make changes to the pipeline, and it can also make it difficult to troubleshoot problems.

#### 3. Siloed and hyper-specialized ownership
Siloed and hyper-specialized ownership refers to the practice of assigning specific data domains or components of the data platform to individual teams or individuals with specialized expertise. Each team or individual takes ownership and responsibility for their assigned area, ensuring focused attention and deep knowledge in that particular domain.

![siloed](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/data_mesh_3.jpg?raw=true)

Siloed ownership can sometimes result in challenges related to data integration. It requires coordination and collaboration between different teams or individuals to ensure seamless integration and consistency across data domains. Proper data governance practices and communication channels are essential to mitigate these challenges.

In a hyper-specialized ownership model, there is a risk of knowledge becoming concentrated within specific teams or individuals. This can pose challenges during employee turnover or when sharing expertise across the organization. Implementing knowledge sharing programs and succession planning strategies can help mitigate these risks.

Siloed ownership may lead to overlapping responsibilities or gaps in ownership between different data domains. Careful planning and communication are required to define clear boundaries and ensure that all areas are adequately covered.

## The next generation enterprise data platform architecture

Introduced by **Zhamak Dehghani**, a distributed data mesh provides a way to reconcile and hopefully address the challenges associated with previous data architectures, which are usually hamstrung by data standardization challenges between data consumers and producers.

Data mesh is a data platform architecture that allows end-users to easily access important data without transporting it to a data lake or data warehouse _and_ without needing expert data teams to intervene. Data mesh focuses on decentralization, distributing data ownership among teams who can manage data as a product independently and securely —reducing bottlenecks and silos in data management and enabling scalability without sacrificing data governance.

The next enterprise data platform architecture is in the convergence of _Distributed Domain Driven Architecture_, _Self-serve Platform Design_, and _Product Thinking_ with _Data_.

![mesh](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/data_mesh_4.jpg?raw=true)
