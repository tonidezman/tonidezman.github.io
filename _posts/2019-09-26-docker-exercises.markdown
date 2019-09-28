---
layout: post
title:  "Docker Exercises"
date:   2019-09-26 09:00:00 +0200
categories: Exercises
---

# this is work in progress

Inspired by Julia Evans's [exercises](https://jvns.ca/blog/2019/08/27/curl-exercises/) I created this docker exercises to gain the muscle memory and understanding of docker commands. Note that these exercises are repetitive on purpose. You should do this exercises 3 days in a row and one more time after a week. Hints and answers are at the bottom of the page.

Docker exercises:

x. Show docker containers stats (CPU, Memory, Disk etc.)
x. How would you get detailed information about docker container?
x. List all docker container sub-commands.
x. List all docker container run flags.
x. List all the volumes
x. How would you delete all volumes except the ones that are currently used by running containers?
x. How would you list all docker images. There are two ways of doing this. Do both.
x. Show detail information about the image


Docker exercises for Rails developers:

1. Run simple ruby script `ruby -e "puts 'Hello, World'" in docker container.
2. List running containers.
3. List all containers (running and terminated).
4. How would you do cleanup containers meaning removing terminated container.

5. Run the command from first exercise so that the container is also cleaned up.
5. User --rm flag
5. docker run --rm ruby:2.6 ruby -e "puts 'Hello, World'"

6. create rails app from docker container. App files need to be seen on your local machine
6. use -v (volume)
6. docker run -it --rm -v ${PWD}:/usr/src/app ruby:2.6 bash  --> then you can install and run rails

7. How would you build image from current dir
7. use build command
7. docker build .

8. Describe a build command
8. /
8. docker build [options] path/to/build/directory

9. How would you list all the images
9. /
9. docker images

10. Create rails project and build an image
10. /
10. /

11. run the image from exercise 10 on port 3000. Quit server and run server on port 7000
11. user -p and -b options
11. docker run --rm -p 3000:000 <image id> bin/rails server -b 0.0.0.0

12. How would you create image name for the already existing "image id"?
12. look at recent images `docker images | head` and use tag docker command
12. docker tag <image id> rails_app

13. How would you remove dangling images (images that have <none> in name and tag)
13. use images with filter option and dangling equal to true
13. docker rmi $(docker images -f "dangling=true")

13. Can you add multiple tags to repository (image name)?
13. /
13. yes

13. Create an image with multiple tags as option.
13. use -t option multiple times
13. docker build -t first_name:latest -t second_name:1.0 .

14. How would you write CMD command in Dockerfile `bin/rails server -b 0.0.0.0`?
14. /
14. CMD["bin/rails", "server", "-b", "0.0.0.0"]

15. Create Dockerfile from scratch that would generate new rails project with the default command
15. /
15. /

15. List all the rake tasks from your rails app. Remember to clean up the generated container with
15. use --rm
15. docker run --rm <image> bin/rails -T

16. How would you handle secrets with docker
16. You need to somehow ignore the secrets
16. in case of rails you should ignore master.key and any other secret file i.e. .env files

17. Create docker-compose for our rails app from scratch
17. /
17. /

18. What does `docker-compose up` do?
18. /
18. Lots of things:
 - Creates a separate network for the app
 - Creates any non-locally mounted volumes ie Database
 - Builds an image for any services with a build directive
 - Creates containers
 - Launches containers

19. How would you stop all docker-compose services? How about just one service?
19. use stop command
19. docker-compose stop <service_name>

19. Run command to see docker-compose logs
19. use -f for following the logs
19. docker-compose logs -f <service_name>



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
