- #Work #Wonders-Corp
- Description : Git, Jenkins, Docker, etc. notes when deploying
-
- ## Jenkins Job
	- There are different scenarios on how to deploy changes, especially when there are other existing builds that will be affected.
	- It is best to review first the project's/repository's deployment process like what environments it is currently being deployed, if there are other teams working on the said projects, and how to rollback if an error occurred after deployment.
	- The following are the different scenarios for deploying and performing a rollback :
	- ### Backend Service
		- These applications usually are being promoted in different status in [Jarvis Jenkins](http://jarvis.letsdochinese.com/jenkins/). And then there is a status to upload docker image to [PRODJenkins](http://prod-jenkins.letsdochinese.com:8080/). In the PROD Jenkins, this is where the backend service Docker image are being deployed to the PROD servers.
		- #### Promoting to QA, STAGING, and Upload Docker Image To PROD (and TRAINING?)
			- Like the **content-config-server**, these applications are being promoted in **QA**, **STAGING**, and **PROD as Docker Image**. But first analyze the **Build History** of the job to take consideration of other devs/teams build.
			- ![image.png](../assets/image_1643854152418_0.png)
			- For example,
				- the build number to be deployed is **#140**
				- the last build that was deployed in PROD is **#135**.
				- ![Screenshot 2022-02-02 213632.png](../assets/Screenshot_2022-02-02_213632_1644361201056_0.png)
-
-
-