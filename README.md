# mongo_deployment
## 1. Create the backend
### a. mongodb_deployment.yml
The deployment file should contain the MongoDB image and the environment variables for username and password authentication. The default port number of mongodb is 27017.
A secret file should be configured with the deployment file for authentication.

### b. mongodb_service.yml
### c. mongodb_secretes.yml
NOTE: The secret file should applied before the deployment application.

## 2. Create the frontend
### a. mongoexp_deployment.yml
### b. mongoexp_service.yml
### c. mongoexp_configmap.yml
A configmap file contains the configuration which is not required to be encrypted like secrets file. It contains the database endpoint which is redirected to the database service. The benefit of connecting the database url to the service endpoint instead of the database ClusterIP is that the service file is immutable and in case the ClusterIP changes, it will be automatically updated in configmap file of mongoexpress 