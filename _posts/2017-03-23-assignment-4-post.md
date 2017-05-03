---
layout: post
title: "Assignment - 4 : Global Transaction Manager"
author: "Thanmai Bindi"
---

## Problem Statement
- How to implement Two-phase commit in a distributed environment. How to make sure that the Prepare phase and the Commit phase takes place successfully. How the architecture fits in with the two phase commit.

## Possible Solution:
- Considering that two microservices has same schema for implementation simplification we created a student microservice and student database. In Two-Phase protocol, microservice will talk to a global transaction manager. Global Transaction manager ensures the two phases takes place with no error. For this to happen Global Transaction Manager should have direct access to all the database schemas and also it should hold the relation dependencies across different databases. 
- Example:
- Microservice User wants to add a new user to its database. Microservice User calls Global Transaction Manager(GTM) to add a new user. 
- GTM will know before hand about all other services which has user dependency. 
- GTM will start prepare phase to Email Database.
- Once GTM receieves the acknowledgement it proceeds to perform Commit.
- Once commit succeeds on the Email Database it commits on the User Database.

## Solution Evaluation:
- This architecture is perfectly fine if we were to use one Manager to manage database and all services talk to the GTM to perform any sort of database operation. There are 2 flaws in this architecture, First: In a distributed architecture each microservice should be tightly coupled with it's database and it shouldn't access other manager to talk to it's own database. Second: Global Transaction Manager is a single point of failure hence maintenance, modification and availability all falls at one point.

## Conclusion:
- Although Global Transaction manager promises Immediate Consistency it is not the right architecture to use in a distributed microservice. 
	
## Commit URL.
These are some of the commits:
	[Two-Phase Commit Implementation using Global Transaction Manager](https://github.com/supreeth90/two_phase_commit)

## Apache Airavata developer’s mailing list. 
	None

## Apache Airavata Jiras that you created or commented on.
	None

## Git pull requests that you made to Apache Airavata’s repo.
	None