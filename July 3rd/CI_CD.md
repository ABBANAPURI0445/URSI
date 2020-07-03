# CD:
 ## Docker Job: Docker Slave 
  * write a Dockerfile and Push to Github 
   1. clone docker file 
   ```
   git clone url(Dockerfile)
   ```
   2. Build image 
   ```
   docker image build -t gol:1.0 .
   ```
   3 docker image push docker Hub (any remote registry)
   ```
   docker login -u username -p password
   docker tag gol:1.0 abbanapuri0445/gol:1.0
   docker push abbanapuri0445/gol:1.0 
   ```
 ## Kuberenets Job: K8s Slave
   * write manifest file(yourhubusername/verse_gapminder:firsttry) and Push to GitHub
   1. clone manifest 
   ```
   git clone url
   ```
   2. apply the manifest file to Kuberenets master
   ```
    kubectl apply -f deployment.yaml
    kubectl apply -f Service.yaml
   ```

## CI:
 * CI stages , upto Jfrog artifactory
![CI](./CI-Stages.jpg)
## CD:
 * CD stages docker and K8S
![CD](./CD-stages.jpg)