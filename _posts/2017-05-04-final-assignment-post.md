---
layout: post
title: "Final Report : Two-Phase Commit in Microservices"
author: "Thanmai Bindi"
---

## Problem Statement:
- In a Distributed System which has microservices all performing certain tasks own a database. And each microservice alone has the authority over that database to make changes. But in cases of consistency all of them have to be in sync either immediately or eventually. Gourav and Ajinkya have worked on [Event-Driven Approach](https://gouravshenoy.github.io/apache-airavata/spring17/2017/04/20/final-report.html) which is eventual consistent approach. Considering a case where there may be need for immediate consistency we wanted to explore how to implement that in a distributed environment with just 2 microservices. 

## Possible Solutions:
- Two-Phase Protocol induces immediate consistency. But it works really well in a single architecture. In case of a distributed architecture there are 2 possible solutions to tackle this. In this course we explored these two solutions: 
- Global Transaction Manager that has direct access to all the databases and it has the knowledge of the dependencies between the schema as explained in the diagram below. Each and every transaction should go through the Global Transaction Manager to complete:
![Global Transaction Manager](https://github.com/tbindi/tale/tree/master/images/GTM.jpg )

- There is another architecture where there is no need for a Global Transaction Manager. This has thrift calls between the two services that communicates from Service A within a single transaction:
![Two Phase Commit Protocol](https://github.com/tbindi/tale/tree/master/images/Basic.jpg )

## Solution Evaluation:
- Both architectures have its disadvantages:
- Architecture - 1 is perfectly fine if we were to use one Manager to manage database and all services talk to the GTM to perform any sort of database operation. There are 2 flaws in this architecture, First: In a distributed architecture each microservice should be tightly coupled with it's database and it shouldn't access other manager to talk to it's own database. Second: Global Transaction Manager is a single point of failure hence maintenance, modification and availability all falls at one point.
- Architecture - 2 has dependency over syncing. In continuous deployment of services there may be a new database that comes with it. But before any operation all the database schemas should be in sync. With the immediate consistency over distributed microservice let's say there is a service that goes down then there will be a stall over all the database related operation. Also if there is a service that will be removed and a new instance of the same service is brought up or upgraded then there should be some kind of sync that should be performed with the new database to make sure that it is in the same level as other databases.

## Conclusion and Recommendation:
