---
layout: post
title: "Assignment - 3 : Two - Phase Commit Intro"
author: "Thanmai Bindi"
---

## Problem Statement
1. What was the problem you tried to solve?
- In a given scenario of the distributed architecture what are the pros and cons of Two-Phase Commit. How to evaluate the consistency issue in case of microservices. 
2. How did you solve it?
- Consider the same architecture as that of the Event-driven approach. We have an Order Service and a Customer Service with their respective databases. But instead of the Message Broker to communicate the events between the two services, we will talk about the Two-phase commit approach.
3. How did you evaluate your solution?

- ### Pros:
	- In an environment which has many databases that get affected. It is good to treat them as transactions. Global transactions span on one or more transactional resources, and enlist them all in a single transaction.
	- Prepare phase can be considered as a dry-run phase to check if the commit is allowed by all the components involved in the system.

- ### Cons:
	- The transaction manager is a single point of failure. If it fails, then the services will never be able to resolve their transactions.				
	- This protocol is a blocking protocol. The manager will block till it receives the messages from the services which would imply that the locks and resources held by it will not be released till it receives a reply.				
	- If any of the services vetoes the commit, then all the services are asked to perform a rollback on their databases. This ensures consistency among partitions. But being a blocking protocol, this mechanism does not ensure good availability.

4. Conclusion
- We know that web services cannot ensure - consistency, availability and partition tolerance. They can, at most, support only two out of the three. ACID, as we know, provides consistency for partitioned databases. If we have to achieve availability instead, we can think of BASE (basically available, soft state, eventually consistent). This basically argues that it is better to have availability along with eventual consistency rather than compromising on availability on the whole. As previously discussed, we can implement an event driven architecture to fulfill this purpose.

## How to Run.
	None
	
## Commit URL.

Wiki Page:

- [Two-Phase Commit in detail](https://github.com/airavata-courses/spring17-microservice-data-management/wiki/Two-Phase-Commit-Explained)

## Apache Airavata developer’s mailing list. 
	None

## Apache Airavata Jiras that you created or commented on.
	None

## Git pull requests that you made to Apache Airavata’s repo.
	None