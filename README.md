# plc3
Product life cycle sample e2e environment


Steps:
in Github Create <name> repository and create the file required but the repository is not initialized (image2.png)
Clone the repository locally in this case a window machine, this will copy the file created in the repository (image21.png)
Git push which will ask for login credentials once supplied the modified content of the file cloned will be ready to be pushed to the said repository (image7.png)
Git commit will make sure the modified content is updated to the Github repository as well (image.png)
Since the repository related is set, now Jenkins needs to be setup and make sure its running and accessible via 8080 port by default (image22.png, image10.png)
Configure first job, in this example, job2, this will do the following : If any developer commits code in Dev1 branch, this job is immediately triggered and will create a Testing environment Docker-Httpd environment and expose port 8081. and Copy the folder contents of entire contents of dev1 repository folder to Testenv folder which is mounted to htdocs folder of TestEnv httpd docker container. So that the latest modification committed by the Dev will be made available for testing as soon as its committed.
Running ngrok to make this machine (at port 8081) available globally even if the QAT available remotely. (image6.png, image25.png image1.png)
Configure next job which is realted to Production Environment. in this case this is job3, this will do the following: Once Job2 is over this job3 project will be automatically triggered. This will create a production environment Docker-Httpd environment and expose port 8082. and Copy the folder contents of testenv to prodenv folder which is mounted to htdocs folder of ProdEnv httpd docker container. Note: This is supposed to be triggered by the QAT (once test automation concepts are clear this will be implemented) (image8.png image24.png)
now as a final step of this plc, configure job3 which will make sure the Testing environment is success, then that is moved to Prod environment as well. That is also deployed and successful. hence trigger an email to the recipients. in this case this is job1. this will do the following: This job will be triggered based on job3 success and will trigger an email notification to the concerned about the build success, build failure and an separate email about which developer broke the build. (image16.png)
All jobs success, accessing Testing environment and Production environment using ports 8081 and 8082 respectively as created with Docker Httpd containers (image18.png image27.png image10.png image11.png image12.png )
