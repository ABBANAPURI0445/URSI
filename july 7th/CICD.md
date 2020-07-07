```
FROM tomcat:8 
ARG user
ARG password
ARG url
RUN wget --user=$user --password='$password'  $url
RUN mv *.war gol.war && cp gol.war /usr/local/tomcat/webapps
EXPOSE 8080
CMD [ "catalina.sh","run"]
```

```
stage('buildimage'){
withCredentials([usernamePassword(credentialsId: 'jfrog', passwordVariable: 'password', usernameVariable: 'user')]) {
    docker image build --build-arg user=$user --build-arg password=$password --build-arg url=http://52.10.220.219:8082/artifactory/GOL/gameoflife$BUILD_NUMBER.war -t gol:$BUILD_NUMBER.0 . 
}
}
```


node('docker') {
   stage('clone dockerfile') {
    git 'https://github.com/ABBANAPURI0445/docker-ursi.git'
}
  stage('build docker image'){
    withCredentials([usernamePassword(credentialsId: 'jfrog', passwordVariable: 'password', usernameVariable: 'user')]) {
    docker image build --build-arg user=$user --build-arg password=$password --build-arg url=http://52.10.220.219:8082/artifactory/GOL/gameoflife$BUILD_NUMBER.war -t gol:$BUILD_NUMBER.0 . 
}  
  }
  stage('docker login'){
      withCredentials([usernamePassword(credentialsId: 'Dockerid', passwordVariable: 'dockerhubpassword', usernameVariable: 'dockerhubuser')]) {
     sh "docker login -u $dockerhubuser -p $dockerhubpassword"
}
  }
 stage('docker image push'){
    sh label: '', script: '''docker tag gol:${BUILD_NUMBER}.0 abbanapuri0445/ursi:${BUILD_NUMBER}.0
docker push abbanapuri0445/ursi:${BUILD_NUMBER}.0'''
  }
  }





