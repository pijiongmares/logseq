- #Wonders-Corp
- Description : Git, Jenkins, Docker, etc. notes when deploying
  collapsed:: true
-
- ## Jenkins Job
	- There are different scenarios on how to deploy changes, especially when there are other existing builds that will be affected.
	- It is best to review first the project's/repository's deployment process like what environments it is currently being deployed, if there are other teams working on the said projects, and how to rollback if an error occurred after deployment.
	- The following are the different scenarios for deploying and performing a rollback :
	- ### Backend Service
		- These applications usually are being promoted in different status in [Jarvis Jenkins](http://jarvis.letsdochinese.com/jenkins/). Then there is a status to upload it to [PRODJenkins](http://prod-jenkins.letsdochinese.com:8080/). In the PROD Jenkins, this is where the backend service Docker image are being created and deployed to the PROD servers.
		-
		  ####