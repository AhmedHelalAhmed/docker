```docker 
# this will run and close immediately
docker run node
```

```docker 
# this will run in interactive mode
docker run -it node
```

```docker
# this will run in detached mode and keep it running
docker run -it -d node
```

```docker 
# this will close immediately you need to run it in interactive mode
# confident_ride is the container name
docker exec confident_ride npm init
```

```docker 
# this will run in interactive mode but in container
docker exec -it confident_ride npm init
```

```docker 
# this will stop the container
docker stop confident_ride
```

```docker 
# this will override the default command and will execute npm init
docker run -it node npm init
```

```docker
# Run service name <npm> + command
# Using run it will create a container and shut it down not removing it 
# If you want to remove it use rm
docker-compose run npm init
docker-compose run npm install express --save

# To remove the container use rm like that
# so once the command is done it will be remove container
docker-compose run --rm npm init

# to remove all containers we use
docker container prune

```