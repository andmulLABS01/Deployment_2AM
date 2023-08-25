
<h1 align="center">Jenkins_Deployment-2<h1> 

# Jenkins Deployment 2
August 26, 2023

By: Andrew Mullen

## Purpose:

Demonstrate the ability to run a Jenkins build and manually deploy to Elastic Beanstalk

## Steps:

### 1. Create your own Jenkins Server and install the following on the server:
   - Install "python3.10-venv"
   - Download and install the Jenkins plugin "Pipeline Utility Steps." 

### 2. Create and run a Jenkins build for the application

- Jenkins is the main tool used in this deployment for pulling the program from the GitHub repository, building, testing, and packaging the files to be deployed to Elastic Beanstalk.
- A Jenkinsfile is used by Jenkins to list out the steps to be taken in the deployment pipeline.

- Steps in the Jenkinsfile are as follows:
  - Build
    - The environment is built to see if the application can run.
  - Test
    - Unit test is performed to test specific functions in the application
  - Packaging the output files
    - Input message asks for confirmation to go to the next step of packaging the files
	- Unit then zips the files that can be downloaded and manually deployed to Elastic Beanstalk

### 3. Observe the pipeline stages via the console output and document what occurred

- The most recent code (that is saved to GitHub) is pulled into Jenkins
    - Using credentials
- The Build Stage built the environment for the application to run
    - See Troubleshooting for errors and resolution
- The Test Stage performed tests and found no errors
- The Packaging Stage, after receiving confirmation, zipped the files

### 4. Extract the zip from Jenkins

- In Jenkins
    - Click the successful build.
	- Cick "Workspaces" and click the file path link
	- Click "all files in zip" at the bottom of the page

### 5. Manually deploy to Elastic Beanstalk

- Deploy the zip file to Elastic Beanstalk
![alt text](https://github.com/andmulLABS01/Deployment_2AM/blob/main/dp2_error.PNG)

![alt text](https://github.com/andmulLABS01/Deployment_2AM/blob/main/dp2_error.PNG)

## System Diagram:

To view the diagram of the system design/deployment pipeline, click [HERE](https://github.com/andmulLABS01/Deployment_2AM/blob/main/Depoyment2.drawio.png)

## Issues/Troubleshooting:

Jenkins could not move to the test phase of the Jenkinsfile

Resolution Steps:
- Check the Console Output in Jenkins
  - Click the Build, Console output
- Discovered the following:
  - Python3.10-venv not installed
  - ensurepip not available
- Installed Python3.10-venv on the terminal
  - `sudo apt install python3.10-venv`
- Rerun Jenkins build and was successful 


![alt text](https://github.com/andmulLABS01/Deployment_2AM/blob/main/dp2_error.PNG)


## Conclusion:

There are some optimizations that can be made to this deployment.  One can be automating the creation of the Jenkins server.  Many advancements are created in response to issues that the current generation of technology faces. The use of Virtual Machines was a large improvement over hosting applications on dedicated physical machines. It solved many problems but also had several of its own. Containerization created lighter, more portable, and more reliable applications by removing configuration drift from the equation. Many companies would benefit from containerization but as time progresses, more people utilize it, and more issues are found, I'm sure that eventually technology will evolve again and an even more efficient system will take its place.
