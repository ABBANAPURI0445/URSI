##Azure DevOps:
 1. its CICD tool
   Azure devops service  -->  cloud Provider 
   azure devops server  --> we need to install on windows server



## Azure devops concepts:
  1. Azure Repos --> remote repository like github , bitbucket
  2. Azure Boards -- > jira , service now --> project management 
  3. Azure Pipeline: 
      1. Build Pipeline  --> clone code and build source code build tools
      2. Release pipeline  --> deploy into dev and test , prod
    hosted agent 
    self hosted agent
  4. Test Plan
  5. Azure artifact : 

CICD:
  1. build Piplie 
  2. azure artifact 
  3. Release Pipeline 

* yaml
* freestyle
* pipeline 
classic  -- 
yaml pipeline -- 




* build java project using azure devops 
   1 clone source code
   2 build java project by using maven 




Demo:
  * deploy java application in webapps (elastic beanstack in aws)
```
az group create --location centralus --name myapp-rg
az appservice plan create -g myapp-rg -n myapp-service-plan --is-linux
az webapp create -g myapp-rg -p myapp-service-plan -n gol-app-deploy --runtime "TOMCAT|8.5-jre8"

```



azuure repos and boards
azure build and release pipeline
deploy
 .net application
 java application  webapps , linux vm

agents --> 
$200 --> 1 month
750 hours --> per -- b1s --t2.micro 1gb and 1cpu 
12 months 
