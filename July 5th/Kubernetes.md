* write Dockerfile
* Push to Github
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
# Kubernetes:
  Lab SetUp:
    * create K8s Cluster
       clusters: Kubeadm , EKS
    * In This CICD i use Eks Cluster 
  ## EKS Cluster:
     * Login AWS Cosole
     * Setup EKS Cluster
  [eks cluster](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)
  1. Launch EC2 machine (kubectl) (t2.micro)
  2. Login into EC2 machine and Install the AWS CLI 
    Please run below commands as Ubuntu user 
   ```
   sudo apt-get update
   sudo apt-get install awscli -y
   ```
  3. Configure AWS 
     * Create IAM User
       We need access and Secret key
       AKIATBPXLQH3KSJ4FZE5
       NL7d/vi2hvl+oHg8goUVd+gdpBnGLJDBiGQCMf3h
    * run Below command on Ec2 machine
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

## Master-slave setup:
  * jenkins master , kubectl slave(where we install kubectl) 
  * 
