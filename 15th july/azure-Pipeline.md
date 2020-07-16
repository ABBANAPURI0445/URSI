## Azure Pipeline:
1. Deploy .net application in windows iis web server 
 ```
   Build Pipeline (dll or exe)
   artifact (dll or exec)
   Release Pipeline (deploy dll or exe into  IIS web server from artifact)
 ```
## Steps:
 1. Create Project
 2. Azure Repos (clone or import source) 
    ```
    https://github.com/GitPracticeRepo/JenkinsBuildExample
    ```
 3. Configure your pipeline (buid pipeline)
    1. select repository
    2. choose agent (microsoft hosted agent or self hosted agent) for build code
      ```
      ASP.net agent
      ```
 4. save pipeline project 
 5. create release pipeline
 6. add deployment group (you will get powershell script)
    ```
    1. luanch windows machine 
    2. login into windows machine
    3. open powershell as admin and execute powershell script