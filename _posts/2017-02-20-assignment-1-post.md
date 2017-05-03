---
layout: post
title: "Assignment - 1 : Laravel Portal"
author: "Thanmai Bindi"
---

## Problem Statement:
- To understand Laravel Portal working and to deploy using CI/CD methodologies. Setting up laravel on a remote Amazon instance using Docker.

## Possible Solution:
- Installed Laravel on local machine first to understand more about the dependencies of the laravel portal. Some of the dependencies listed were: php, composer and dockerizing it. First we should deploy in docker make sure the dependencies are present before deploying and starting the framework or the actual code. This task can be done using `before-install.sh` script.

## Solution Evaluation:
- Once we establish CI/CD platform using Docker with use of Travis and Shell script we should be able to control how the code can be deployed smoothly to different Amazon instances across different areas. There is no evaluation of this solution against other as this is the dependency install.

## Conclusion:
- There should be a setup of the docker container on the amazon instances we are deploying to. Once the docker is up to date we can install php and composer. Once these operations are successfully completed we were able to start the docker service.

## How to Run.
- Clone the project: https://github.com/airavata-courses/spring17-laravel-portal
- Make changes and commit. Once you are certain that the commit does not break the `before-install.sh` script you can push the code. This triggers the Travis to deploy the repository to a docker container and start the service on Amazon instance.
	
## Commit URL.

These are some of the commits:

- [Laravel-logging](https://github.com/airavata-courses/spring17-laravel-portal/commit/cae55efb61817c25295dbdd26365233d1d890cf9)

- [Modified before install script](https://github.com/airavata-courses/spring17-laravel-portal/commit/b387bfb4fa2dc1d7104a880919eb3214f991325f)
	
- [Run Laravel by exposing the port number](https://github.com/airavata-courses/spring17-laravel-portal/commit/1929641c4c5cc826f60ac339e15b93dc1db9e761)

- [Modified to individual port number and individual logging](https://github.com/airavata-courses/spring17-laravel-portal/commit/450223b06e1ad7fc8adc084ed1b2144b380dd8de)


## Apache Airavata developer’s mailing list. 
	None

## Apache Airavata Jiras that you created or commented on.
	None

## Git pull requests that you made to Apache Airavata’s repo.
	None