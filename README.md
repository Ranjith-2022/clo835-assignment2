## Assignmnet 2 ##


scp -i assignment2 app-deployment.yaml app-pod.yaml app-replica.yaml app-service.yaml mysql-pod.yaml mysql-deployment.yaml mysql-replica.yaml mysql-service.yaml kind.yaml init_kind.sh 3.231.161.51:/tmp


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



