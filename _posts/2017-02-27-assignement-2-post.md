---
layout: post
title: "Assignment - 1 : Laravel Portal Deployment"
author: "Thanmai Bindi"
---

## Problem Statement -- A report of what you did and your outcomes.
1. What was the problem you tried to solve?
- Deploying of Laravel on Amazon instance and containerizing the portal in docker. I had to make the portal work with the install scripts which will not be dependant on the system that it's running.
2. How did you solve it?
- Docker scripts was used to run and build the docker image. This pulls the latest code, builds and deploys it to the container. This deletes the container and the image before deploying. Even before the zip is deployed this will install the dependencies like Composer and Zip. After changing the permissions of the folder, the `composer install` downloads all the package. Then copy `.env.example` to `.env` to generate key and run the server. 3 portals will be exposed 3000, 4000 and 5000 for laravel portal.
3. How did you evaluate your solution?
- Portal once exposed from docker it can be accessed outside as well. So once you go to the particular portal:port via browser this will be open.
4. Conclusion
- There should be a setup of the docker container on the amazon instances we are deploying to. Once the docker is up to date we can install php and composer. Once these operations are successfully completed we were able to start the docker service.

## How to Run.
- Clone the project: https://github.com/airavata-courses/spring17-laravel-portal
- Make changes and commit. Once you are certain that the commit does not break the `before-install.sh` and `install.sh` script you can push the code. This triggers the Travis to deploy the repository to a docker container and start the service on Amazon instance.
	
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