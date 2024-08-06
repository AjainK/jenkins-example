# jenkins-example

Steps to automate code deployment in jenkins

1.Setup
=> Install Jenkins
=> Go to Dashboard -> Manage Jenkins
=> Check Available and Installed Plugins.
=> Search for Github Integration Plugin from Available Plugins and Install it.

2. Checkout Code from Repo

=> Create new jobs -> Give Job Name -> Freestyle Project
=> Under Advanced -> Select Use Custom Workspace -> Provide the directory path where you want to checkout the git code.
=> Under SCM -> Select Git -> Give the path to the Git repo you want to checkout and configure the github account credential.
=> Run the job. It will pull the checkout the contents  of the github repo to the directory path you have given. Verify the step by checking the directory path for the code .

3. Automate the checkout

=> Go to the same job created and Under Build Trigger -> Poll SCM give corresponding cron expression and save.
=> Based on the schedule frequency given the pipleine will poll the github repo and checkout the code.

4. Build

=> Create a new job 
=> Under Advanced -> Select Use Custom Workspace ->  Provide the directory path where the code has been checked out
=> Under Build steps choose windows/shell based on your OS and give mvn clean install
=> Save and Run

5. Pipleine Creation

=> Install Build pipeline plugin
=> Create a new pipeline
=> Initial Job => Code checkout
=> Go to Code checkout job and Post Build Actions -> Projects to Build -> Select Build job and save.
=>Test the pipeline by changing code and pushing to repo. 
=>This in turn will trigger the pipeline

7. Deploy to cloudhub

=> Add cloudhub configurations under mule maven plugin under pom.xml
=> Configure username and password, environment,workers, workerType,applicationName,muleVersion,password
=> Create new job for deploy
=> Under Advanced -> Select Use Custom Workspace ->  Provide the directory path where the code has been checked out.
=> Build step -> mvn package deploy -DmuleDeploy and save
=> Add deploy step to the  pipeline (Go to Build job , configure -> Post Build action and choose Deploy Job and save).





Overall Setup Steps :

1. Create a job to pick the code from repo and checkout to a directory we want. 
2. Create a job to run maven install on the checkedout directory.
3. Create a job to run mvn deploy .
4. Create a pipeline - Point Initial Job to the checkout job.
5. In the code checkout job and under Post Build Actions and choose the build job.
6. In the Build Job under Post Build Actions code the deploy job.





