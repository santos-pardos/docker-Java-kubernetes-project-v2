## Java App - Docker - K8s in AWS EKS
```
kubectl cluster-info
sudo apt install default-jdk -y
sudo wget https://dlcdn.apache.org/maven/maven-3/3.9.4/binaries/apache-maven-3.9.4-bin.tar.gz
sudo tar -xvzf apache-maven-3.9.4-bin.tar.gz
sudo cp -r apache-maven-3.9.4 /opt/maven
sudo nano /etc/profile.d/maven.sh

export JAVA_HOME=/usr/lib/jvm/default-java
export M2_HOME=/opt/maven
export MAVEN_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}

sudo chmod +x /etc/profile.d/maven.sh
sudo source /etc/profile.d/maven.sh
mvn -version

git clone https://github.com/santos-pardos/docker-Java-kubernetes-project-v2.git
cd docker-Java-kubernetes-project-v2
cd shopfront/
mvn clean install
docker build -t shopfront .
docker images
docker login
docker push shopfront


EKS (see others videos to connect with Cloud9 to EKS Cluster)
Version 1 
kubectl get pods
kubectl get deployments
kubectl get svc
kubectl apply -f productcatalogue-service.yaml
kubectl apply -f shopfront-service.yaml
kubectl apply -f stockmanager-service.yaml
kubectl get deployment
kubectl get pods -o wide
kubectl get svc
kubectl get svc shopfront
http://<ec2-public-ip>:xxxxx   (xxxxx port in the service)
kubectl get svc productcatalogue
http://3.84.251.55:xxxxx/products   (xxxxx port in the service)

Version 2
kubectl get pods
kubectl get deployments
kubectl get svc
kubectl apply -f productcatalogue-service.yaml
kubectl apply -f shopfront-deployment.yaml
kubectl apply -f shopfront-service.yaml
kubectl apply -f stockmanager-service.yaml
kubectl get deployment
kubectl get pods -o wide
kubectl get svc
kubectl get svc shopfront
http://<alb-public-ip>
```

### Links
https://medium.com/@mudasirhaji/how-to-deploy-java-application-in-kubernetes-using-aws-ec2-214163a1a921

https://repost.aws/knowledge-center/eks-kubernetes-services-cluster
