**** Assignmnet 2 ****

Docker Installation 

sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl status docker

Access 

sudo chmod 666 /var/run/docker.sock
sudo usermod -a -G docker ec2-user
aws configure
sudo vi ~/.aws/credentials


scp  copy

aws docker image push command

docker pull mysql

docker pull app

chmod 777 ./init_kind.sh 

./init_kind.sh

** The local K8s cluster **

kubectl get nodes

kubectl cluster-info



** Namespace **

kubectl create ns app-ns

kubectl create ns mysql-ns

** Pod **

kubectl apply -f app-pod.yaml

kubectl apply -f mysql-pod.yaml 

kubectl apply -f app-service.yaml

kubectl apply -f mysql-service.yaml

** Retriving pods **

kubectl get pods -n app-ns

kubectl get pods -n mysql-ns

** Retriving Service **

kubectl get services

** Connecting services **

kubectl exec -it application-pod -- /bin/sh

kubectl port-forward pod/application-pod 8080:8080

curl localhost:8080

kubectl logs application-pod

kubectl logs mysql-pod


** Replica Set **

kubectl apply -f app-replica.yaml 

kubectl apply -f mysql-replica.yaml

kubectl get rs

** Deployment **

kubectl apply -f app-deployment.yaml 

kubectl apply -f mysql-deployment.yaml    

kubectl get deployments

** Deployment Version Change **

kubectl rollout history deployment application 


** DELETE **

kubectl delete services --all 

kubectl delete pods --all 



