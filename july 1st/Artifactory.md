## 1 use cases
* store dependencies  ---> 
* store executables/war exe dll --> these builds generate when run mvn package --> war/jar/ear  --MSBuild --> exe , dll
* docker images  --> docker image build -t image:1.0 . --> image

## 2 artifact tools:

* jfrog artifactory
* Nexus
* S3 

## 3 how to install Jfrog artifactory

Reference: https://websiteforstudents.com/how-to-install-jfrog-artifactory-on-ubuntu-18-04-16-04/

steps:
  1 lauch EC2 machine (t2.medium) open 8081 22 8082 Ports
  2 install java8



## 4 how to integrate to jenkins 
  1 Install Plugin:  
  * goto jenkins
    goto manage jenkins
      ==> manage plugin
        ==> available
         ==> plugin name: artifactory
           ==> install plugin and restar
  2 goto manage jenkins
       goto configure system
         look at jfrog image




## static code analysis
  
  1. use case
  2. tools in static code analysis
     veracode
     sonarqube
     codecy
  3. how to install sonarqube
     
  4. how to integrate to jenkins
     * install plugin
     * goto system configure 
         look at sonarqube image












   stages:
     1. clone  source code
     2. build 
     3. Publish Junit Test results
     4. archive the Artifact
     5. Static code analysis
        sonarqube
     6. store builds in repository
        Jfrog artifactory 
        Nexus
        S3 
  # Environemnt:
   git , github , jenkins , sonarqube , jfrog artifactory ,maven , docker (create image and push registry) , kuberenets(deploy pods images taken from dockerhub) EKS , (namespace)













