## Containerized Stateless Applications using Kubernetes ##

## Overview

# Assignment: Hosting Containerized Application on KIND Cluster in AWS EC2

## Overview

In this assignment, the goal is to host a containerized application on a KIND (Kubernetes IN Docker) cluster running on an Amazon Linux-based EC2 instance in the AWS environment. The assignment flow includes the following steps:

1. **Deploy Amazon Linux EC2 Instance**: Provision an Amazon Linux-based EC2 instance with sufficient capacity to run the KIND cluster and host the containerized application.

2. **Install Pre-requisites**: Install all the necessary pre-requisites on the Amazon EC2 instance required to host the containerized application on the Kubernetes cluster created by KIND (kind, kubectl).

3. **Create KIND Cluster**: Use the KIND tool to create a Kubernetes cluster.

4. **Deploy Containerized Application**: Deploy the containerized application using pod, replicaset, deployment, and service manifests.

5. **Expose Web Application**: Expose the web application using a Service of type NodePort.

6. **Expose MySQL**: Expose MySQL using a Service of type ClusterIP.

7. **Update Applications**: Update the applications and deploy the new version of the application.


## Tools and Services Used

- **Amazon ECR**: Securely store your container images.
- **Cloud9 IDE** (or your local environment): Develop your application and build container images.
- **Amazon EC2**: Host your KIND cluster.
- **KIND**: Deploy a local Kubernetes cluster.
- **Kubectl**: Communicate with the Kubernetes API Server.
- **AWS IAM** (Identity and Access Management): Grant EC2 instance access to Amazon ECR repository.
- **Terraform**: Optionally deploy the infrastructure.


 #### Docker Installation ####

sudo yum update -y

sudo yum install docker -y

sudo systemctl start docker

sudo systemctl status docker

#### Access ####

sudo chmod 666 /var/run/docker.sock

sudo usermod -a -G docker ec2-user

aws configure

sudo vi ~/.aws/credentials

aws docker image push command

chmod 777 ./init_kind.sh 

./init_kind.sh

#### The local K8s cluster ####

kubectl get nodes

kubectl cluster-info


#### Namespace ####

kubectl create ns app-ns

kubectl create ns mysql-ns

#### Pod ####

kubectl apply -f app-pod.yaml 

kubectl apply -f mysql-pod.yaml 

kubectl apply -f app-service.yaml 

kubectl apply -f mysql-service.yaml 

#### Retriving pods & Service ####

kubectl get pods -n app-ns

kubectl get pods -n mysql-ns

kubectl get services -n app-ns

kubectl get services -n mysql-ns

#### Connecting services ####

kubectl exec -it application-pod -n app-ns  -- /bin/sh 

kubectl port-forward -n app-ns pod/application-pod 8080:8080

curl localhost:8080

kubectl logs application-pod -n app-ns

kubectl logs mysql-pod -n mysql-ns


#### Replica Set ####

kubectl apply -f app-replica.yaml

kubectl apply -f mysql-replica.yaml

kubectl get rs -n app-ns

kubectl get rs -n mysql-ns

kubectl get pods -n app-ns

kubectl get pods -n mysql-ns

#### Deployment ####

kubectl apply -f app-deployment.yaml

kubectl apply -f mysql-deployment.yaml 

kubectl get deployments -n app-ns

kubectl get deployments  -n mysql-ns

kubectl get pods -n app-ns

publicip:30000


#### Deployment Version Change ####

kubectl rollout history deployment application -n app-ns

kubectl get pods -n app-ns

kubectl get pods -n mysql-ns


#### DELETE ####

kubectl delete services --all 

kubectl delete pods --all 



