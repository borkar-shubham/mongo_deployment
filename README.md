# mongo_deployment
## 1. Create the backend
### a. mongodb_deployment.yml
The deployment file should contain the MongoDB image and the environment variables for username and password authentication. The default port number of mongodb is 27017.
A secret file should be configured with the deployment file for authentication.

### b. mongodb_service.yml
The service configuration for MongoDB is used to expose the backend application to the frontend application privately with ClusterIP type of service. It used to listen the traffic at the port 27017 of container and forward it to the port 27017 of the application.
### c. mongodb_secretes.yml
The secrete file contains the username and password in the encrypted format with the type of Opaque service.
NOTE: The secret file should applied before apply the mongodb-deployment file.

## 2. Create the frontend
The frontend application of MongoDB is MongoExpress which is connected to MongoDB at backend through the ConfigMap. It gives the UI to create and manupulate the databases at backend.
### a. mongoexp_deployment.yml
### b. mongoexp_service.yml
### c. mongoexp_configmap.yml
A configmap file contains the configuration which is not required to be encrypted like secrets file. It contains the database endpoint which is redirected to the database service. The benefit of connecting the database url to the service endpoint instead of the database ClusterIP is that the service file is immutable and in case the ClusterIP changes, it will be automatically updated in configmap file of mongoexpress.
---
files must be triggered at the sequence of -
* mongodb_secret.yml
* mongodb_deployment.yml
* mongodb_service.yml
* mongoexp_configmap.yml
* mongoexp_deployment.yml
* mongoexp_service.yml
