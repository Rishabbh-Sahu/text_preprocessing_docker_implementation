# <p align=center>Text pre-processing implemented with docker container</p>
A simplest illustration of deploying any model (or a rule based engine in this scenario) using docker container. The main focus of this repo is to leverage ``Docker Images & containers`` to run/host the solution anywhere. This repo can be thought of as a first building block of a "production grade system" with services hosted on a cloud. Here, a text pre-processing method(can be considered as an ML model) is used, to filter only alphanumeric characters within the input text, for the simplicity and deployed the docker-image with necessary system/libraries dependencies using docker-container. 

#### Steps 
 - Build the docker image (specify a different tag to improve readability -t <tag_name>)
 ```buildoutcfg
docker build -t flask-rest-api .
```
 - You can check and verify the docker image using images params.
```buildoutcfg
docker images
```
 - Run the docker image. Worth to note the mapping of the ports from 5000-local to 5000-docker 
```buildoutcfg
docker run -d -p 5000:5000 flask-rest-api
```
 - To see that the container is in fact running:
```buildoutcfg
docker ps -a
```
 - Run **unit-test** using docker 
```buildoutcfg
docker run flask-rest-api py.test
```
 - To show all the logs for the container 
```buildoutcfg
docker logs <CONTAINER ID OR CONTAINER NAME>
```
 - Stop docker container 
```buildoutcfg
docker stop
```
#### For more docker related commands, follow the link below
https://docs.docker.com/reference/

#### Requesting to the API
```
curl --location --request POST 'http://0.0.0.0:5000/fetch' --header 'Content-Type: application/json' --data-raw '{"text": "what7%$$"}'
```
