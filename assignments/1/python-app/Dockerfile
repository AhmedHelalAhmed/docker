FROM python

WORKDIR /app

COPY . /app

CMD ["python","bmi.py"]

# steps to build and run the container
#  docker build -t python-app:latest .
#  docker run -it python-app
#  Output:
# (1) Metric (m, kg) or (2) Non-Metric (ft, pounds)?
# Please choose: 1
# Please enter your height in meters
# Your height: 170
# Please enter your weight in kilograms
# Your weight: 80
# Your body-mass-index: 0.002768166089965398

# docker run -it --name=container-of-python-app python-app

# docker stop container-of-python-app container-of-node-app


# docker rm 621ec8f803ff dde19877c2f6 40a118cdc5b7 72d3d1360780 20feb78cc3e4
# docker rmi python-app

# docker run --rm -it python-app
