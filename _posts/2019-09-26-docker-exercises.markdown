---
layout: post
title:  "Docker Exercises"
date:   2019-09-26 09:00:00 +0200
categories: Exercises
---

Inspired by Julia Evans's [exercises](https://jvns.ca/blog/2019/08/27/curl-exercises/) I created this docker exercises to gain the muscle memory and understanding of docker commands. Note that these exercises are repetitive on purpose. You should do this exercises 3 days in a row and one more time after a week. Hints and answers are at the bottom of the page.

Let's get started:

1. Run simple ruby script `ruby -e "puts 'Hello, World'" in docker container.
2. List running containers.
3. List all containers (running and terminated).
4. How would you do cleanup containers meaning removing terminated container.

5. Run the command from first exercise so that the container is also cleaned up.
5.
5.


Hints:
1. run `docker run [options] <image> <command>` which creates, runs and stops the container
2. use either docker 'ps' or 'container ls' commands
3. use -a flag
4. use rm command

Answers:
1. docker run ruby:2.6 ruby -e "puts 'Hello, World'"
2. docker ps
3. docker ps -a
4. docker rm <container id> [<container id> ...]
