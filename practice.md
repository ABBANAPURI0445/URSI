## activity 1: Java Project
  * install jenkins (Master) (t2.micro)
  * install maven (Slave) (t2.large) (linux)
  * setup master-slave configuration
  * run java project
    Steps:
     execute below 4 stages
      * clone source code
        git clone https://github.com/spring-projects/spring-petclinic.git 
      * build code  
        mvn package
      * show junit test results
        spring-petclinic/target/surefire-reports/*.xml
      * archive artifact   
       spring-petclinic/target/spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar


## opensource java projects:
   * gameoflife: simple game application
      https://github.com/wakaleo/game-of-life.git
   * Spring-Petclinic: pet project 
      https://github.com/spring-projects/spring-petclinic.git
   * OpenMRS:  Open Medical Record System
      https://github.com/openmrs/openmrs-core.git



   * Shopizer: E-commerce 
     https://github.com/shopizer-ecommerce/shopizer.git

## Two ways: 
 * Freestyle project
 * Pipeline project


dash board screen shots


## activity 2: .Net  Project
  * install jenkins (master) 
  * install MSBuild and nuget (t2.large) (windows-slave)
  * setup master-slave 
  * run .net project
    Steps:
     execute below 3 Stages
       * clone source code
       * restore package using Nuget
       * build code for generate dll file using MSBuild
## Opensource .net Project:
     https://github.com/GitPracticeRepo/JenkinsBuildExample.git
## Two ways
 * Freestyle Project
 * Pipeline Project




test-cases

provide path from pom.xml

 gameoflife-core/target/surefire-reports/*.xml


 gameoflife-web/target/gameoflife.war
                      


gameofgame: 
gameoflife-web/target/*.war   --> archive artifact
gameoflife-web/target/surefire-reports/*.xml  --> Junit Test results
