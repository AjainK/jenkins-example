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








