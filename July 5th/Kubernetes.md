# __Docker__:
* write Dockerfile
* Push to Github
```
node('docker'){
    stages:
      clone dockerfile 
      build docker image
      push to Remote Registry
       store Docker Images in Multiple Places
         DockerHub
         ECR --> Elastic Container Registry aws service
         ACR --> Azure Container Registry azure service
         Nexus
         Jfrog 
}
```
# __Kubernetes__:
  Lab SetUp: \
    * create K8s Cluster \
       clusters: Kubeadm , EKS \
    * In This CICD i use Eks Cluster 
  ## EKS Cluster:
     * Login AWS Cosole
     * Setup EKS Cluster
  [eks cluster setup](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)
  1. Launch EC2 machine (kubectl) (t2.micro) __install openjdk8__
  2. Login into EC2 machine and Install the AWS CLI 
    Please run below commands as Ubuntu user 
   ```
   sudo apt-get update
   sudo apt-get install openjdk-8-jdk -y
   sudo apt-get install awscli -y
   ```
  3. Configure AWS 
     1. Create IAM User
       We need access and Secret key
       
     2. run Below command on Ec2 machine
      ```
      aws configure
      ```
  4. Install Eksctl
  5. Install and configure kubectl
    [kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html) 
  6. Create your Amazon EKS cluster and worker nodes
  ```
    eksctl create cluster \
    --name prod \
    --version 1.16 \
    --region us-west-2 \
    --nodegroup-name standard-workers \
    --node-type t2.micro \
    --nodes 3 \
    --nodes-min 1 \
    --nodes-max 4 \
    --ssh-access \
    --ssh-public-key mykeypair \
    --managed
  ```

## __Master-slave setup__:
  * jenkins master , kubectl slave(where we install kubectl) 
  

### __Continous Integration & Continous Deployment__:
  1. __Continous Integration__
      __stages__:
       1. clone source java code
       2. execute build commands 
       3. Publish Junit test results
       4. archive the artifact
       5. Static code analysis
       6. Store artifact in jfrog
  2. __Continous Deployment/Delivery__
      __stages__:
        1. clone dockerfile 
        2. create image 
        3. push to remote registry
        4. clone manifest files
        5. apply to eks cluster



Complte CICD flow
 * with credentials \
daybuild and night build


docker image build --build-arg src=http://54.187.78.11:8082/artifactory/GOL/gameoflife8.war -t gol:$BUILD_NUMBER.0  .