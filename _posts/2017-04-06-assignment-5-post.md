---
layout: post
title: "Assignment - 5 : Two-Phase Commit in Microservices"
author: "Thanmai Bindi"
---

## Problem Statement
- Implementing two-phase commit without a global transaction manager and making sure that each microservice is the owner of it's own database. Global Transaction Manager was responsible to make sure that the relation of all the attribute over a distributed architecture was consistent. Now, each individual service should be responsible to make sure that other database will be consistent and in sync.

## Possible Solution:
- Since there is no global transaction manager, each service needs to call other services through thrift to make the db transaction. And all the services should implement prepare and commit phase. For this scenario we've taken Customer and Order service. Consider Customer service is issued a create customer. We assume that till this point all the database are in sync and are consistent with each other.
- Steps on how the operation takes place:
- Customer Service opens a transaction. Requests a persist call through thirft service to Order Service.
- Order Service persists and replies with an acknowledgement.
- Customer Service calls Order Service with Commit call through thrift.
- Order Service commits and replies with an acknowledgement. Once the Customer service confirms the commit on all other dependant services it commits on it's own database.

## Solution Evaluation:
- With the immediate consistency over distributed microservice let's say there is a service that goes down then there will be a stall over all the database related operation. Also if there is a service that will be removed and a new instance of the same service is brought up or upgraded then there should be some kind of sync that should be performed with the new database to make sure that it is in the same level as other databases.

## Conclusion:
- We need to look at a sync mechanism that should be present between 2 versions of the database.

## How to Run.
- [Steps to run the code](https://github.com/airavata-courses/spring17-microservice-data-management/wiki/Event-Driven-DB:-Steps-to-Run-Prototype)
	
## Commit URL.

These are some of the commits:
- [Modified event-driven to use thrift calls directly without Message Queue](https://github.com/airavata-courses/spring17-microservice-data-management/commit/68e581d3ce71ff8717a361f6972beb0fe5ad9dd0).

## Apache Airavata developer’s mailing list. 
	None

## Apache Airavata Jiras that you created or commented on.
	None

## Git pull requests that you made to Apache Airavata’s repo.
	None