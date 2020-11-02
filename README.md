# Mongo-app
## Deploying a MongoDB and Mongo Express application

In this tutorial we are going to `deploy` a `MongoDB` and `Mongo Express` applications using the following `Kubernetes` components: 
* `Service` type `clusterIp` - an internal service for our `MongoDB` app (no external requests!)
* `Secret` that contains our DB credentials
* `configMap` that stores our DB url
* `Deployment` - two Deployments one for the `MongoDB` app and one for the `Mongo Express` app. in the Deployment files we are gonna reference both secret and configMap files using `Environment variables` in order to access our DB in a secure way.
* `Service` type `LoadBalancer` - Extarnal service that will allow external requests to our Mongo Express pod.

so with this setup the request flow will look like this:
1. the request comes from the browser.
2. request goes to the External service of the Mongo Express which will than forward it to the Mongo Express pod.
3. pod will then connect to the internal service of MongoDB (thats basically the DB url from our configMap).
4. the service will forward the request to the MongoDB pod where it will authenticate using the credentials (from the secret).

### Pre requirements
* running cluster or`minikube` [installed](https://minikube.sigs.k8s.io/docs/start/)
* `kubectl` [installed](https://kubernetes.io/docs/tasks/tools/install-kubectl/)




#### When all this done, feel free to run the runMe file and go check localhost:8080 for the results :)

## Expected results:
