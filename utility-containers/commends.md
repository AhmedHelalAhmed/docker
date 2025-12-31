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