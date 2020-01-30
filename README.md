# Cloud devops engineer capstone project

In this project, we will implement a full CI/CD pipeline using Jenkins, Docker, Kubernetes, Cloudformation for the provisioning the infractructure.

## Jenkins Installation

## Create EKS kubernetes cluster

## Installing a demo app on Kubernetes
### Install Pipeline AWS
In order to deploy the  containerized app in the EKS cluster, the Pipeline Aws steps plugin will be install. A credential is then created using as usernama the ACCESS_KEY_ID and password the SECRET_KEY_ID.
For futher details, please have a look to the pupeline aws plugin github[Pipeline Aws plugin](https://github.com/jenkinsci/pipeline-aws-plugin)

## Create a replication service and controller
Once the kuberntes cluster, is configured and runned, a replication service and controller is created in order to deploy the dockerized app to the EKS Cluster.  Fore more example on how to deploy an application to eks cluster have a look on theses examples:
- [Deploying a Kubernetes Cluster with Amazon EKS](https://logz.io/blog/amazon-eks/)
- [Capstone project, Cloud DevOps Nanodegree FAQ](https://medium.com/@andresaaap/capstone-cloud-devops-nanodegree-4493ab439d48)


### Use kubectl to see a list of your services:
```sh
kubectl apply -f <controller-name.json>
kubectl apply -f <service-name.json>
kubectl get svc
```

