# Overview
This project is created as part of **Kaiburr Assessment**. Dockerimage used in this project is based on this [repo](https://github.com/shanureddy4/WebApiTask)(Task1). Two pods were created. One for springboot application and another is for mongoDB. With LoadBalancer springboot application is exposed to host machine. mongoDB is accessed with environment variables. To maintain persistent for mongoDB , PersistentVolumeClaim of 100MB is created.
## Getting Started

This project assumes you have kubernetes environment installed in your machine.
### steps to deploy
* Clone the project into your machine
* Go to the project directory. Here before creating deployment we need to have variables declare in the config-map and secret files. So we should apply them first with these commands.<br>
 ``` kubectl apply -f mongo-secret.yaml ``` <br>
 ``` kubectl apply -f spring-config.yaml ``` <br>
 * Now we need to create PersistentVolumeClaim to maintain persistense data.<br>
 ``` kubectl apply -f mongo-pvc.yaml ``` <br>
 * Now deploy application with mongodb. <br>
 ``` kubectl apply -f mongo.yaml ``` <br>
 ``` kubectl apply -f springboot.yaml ``` <br>
 * service for each applications is created along side of their deployment with above files.
 * Now check your service running endpoints with this command
 ``` minikube service --all ``` . This will display all services associated with pods. <br>
## Output
