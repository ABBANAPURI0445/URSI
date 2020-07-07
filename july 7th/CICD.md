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








