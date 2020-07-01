FROM tomcat:8
ADD http://18.237.37.165:8082/artifactory/GOL/gameoflife.war /usr/local/tomcat/webapps
EXPOSE 8080
CMD ["catalina.sh" "run"] 

Dockerhud
----------
* dockerfile put in github
* clone dockerfile
* docker image 
----
docker image build -t gol:1.0 .
----
* push to registry Dockerhub
   gol:1.0
--------

Kubernetes:
-------
deployment.yaml
 in Pod spec 
     image: gol:1.0
--------

* launch ec2 machine and install docker (slave of jenkins)

node('docker'){
    stage("SCM-Dockerfile"){
        //clone dockerfile from github
    }
    stage('docker image'){
        sh 'docker image build -t gol:1.0 .'
    }
    stage("push image"){
        // push image to dockerhub
    }
}

node('kubectl'){
    stage('SCM-deployment-manifestfile-service'){
        git clone url
    }
    stage('apply manifest'){
        sh 'kubectl apply -f deployment.yaml'
        sh 'kubectl apply -f service.yaml'
    }
}

