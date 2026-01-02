```
docker build -t node-dep-example .
```
```
docker run -d --rm --name node-dep -p 80:80 node-dep-example
```
# visit http://localhost/

# connect to ec2 and install docker
```
sudo yum update -y
sudo yum -y install docker
sudo service docker start
sudo usermod -a -G docker ec2-user
```
# Make sure to log out + back in after running these commands.
# Once you logged back in, run this command:
```
sudo systemctl enable docker
```
# Thereafter, you can check whether Docker is available by running:
```
docker version
```

# push to docker hub the image
# comes from repo ahmedhelalahmed/node-example-1
```
docker build -t node-dep-example .
docker images | grep 'node-dep-example'
docker tag node-dep-example ahmedhelalahmed/node-example-1
docker login
docker push ahmedhelalahmed/node-example-1
```
# in ec2
```
docker run -d --rm -p 80:80 ahmedhelalahmed/node-example
```
# you can see the app running on port 80 in http://54.72.161.175/
