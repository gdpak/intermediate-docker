## Saving a docker container

We know the container is an immutable system that means all the changes done inside the container will be lost when you stop and remove the container.

But what if we want to save. Sometimes we just want to keep tweaking a running container until it works as we want it to. We can save the container as an image.

Let's start with running an nginx container

```shell
# run a container mapping TCP port 80 in the container to port 8080 on the Docker host:
docker run -d -p 8080:80 --name nginx-server nginx:1.17.0
```

Check the http://localhost:8080 on browser to see the default nginx page.

![](/imgs/nginx-running.png)

Let's modify the running container, we can do several things such as installing some tools/utilities or making some changes in the existing files inside the container. We will keep the things simple by modifying the default nginx `/usr/share/nginx/html/index.html` file. We will overwrite it with our [own version](./index.html)

```shell
# docker cp copies the content inside the running container
docker cp labs/docker/commit/index.html nginx-server:/usr/share/nginx/html/index.html
```

Reload the browser to see the changes reflected on the webpage http://localhost:8080

### Creating image from the running container
We have updated the contents of the running container and we know they will be there till the time container is running. The container is immutable, to make the changes permanent we have to save the container as an image.

To save the container as image we have to use `docker commit` command:

```shell
# save the changes to my-nginx-server image name
docker commit nginx-server my-nginx-server

# check the docker image list
docker image ls 'my-nginx-server'
```

Stop and remove the running container

```shell
docker stop nginx-server && docker rm nginx-server
```

Start the container from the new image and check the default page on the browser

```shell
docker run -d -p 8080:80 --name nginx-server my-nginx-server:latest
```

Visit http://localhost:8080 to see the default page.

___
## Cleanup

Cleanup by removing all containers:

```
docker rm -f $(docker ps -aq)
```