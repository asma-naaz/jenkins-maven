# TASK-8

# Java Maven Jenkins Build Project

## Purpose
This project is a simple **Java HelloWorld application** built using **Maven** and automated using **Jenkins**. The goal of this project is to understand the basics of Continuous Integration (CI) by setting up a Maven build process inside Jenkins, which is one of the first steps in automating software delivery.

# Step-by-Step Guide
* Step 1:
* Create the Java Application
* Create a directory for your project:

* mkdir -p ~/hello-java-maven/src/main/java
* Create the HelloWorld.java file in src/main/java/:

* nano ~/hello-java-maven/src/main/java/HelloWorld.java
* Paste the Java code into HelloWorld.java and save the file.

# Step 2: Create the pom.xml File
* Create the pom.xml file in the root directory of your project:
* nano ~/hello-java-maven/pom.xml
* Paste the pom.xml content and save the file.

# Step 3: Set Up Jenkins on EC2 Instance
* Start Jenkins using Docker (if not already running):
* sudo docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
* Install Java and Maven inside Jenkins Docker container:

* Run the following command to enter the Jenkins container:
* sudo docker exec -it jenkins bash
* Then, install Java and Maven inside the container:
* apt update
* apt install -y maven
* Install Jenkins dependencies (if needed):
* apt install -y openjdk-11-jdk

# Step 4: Configure Jenkins Job
* Add Maven in Jenkins Configuration:
* Go to Manage Jenkins → Global Tool Configuration.
* Under Maven, select Add Maven and name it Maven 3.8.6.
* Create a New Jenkins Freestyle Project:

# In Jenkins Dashboard, click New Item.

* Enter project name (e.g., java-maven-job), select Freestyle project, and click OK.
* Configure Build Step:

* In the Build section, select Execute shell.

* Add the following commands to build your project from the local path:
* cd /home/ubuntu/hello-java-maven
* mvn clean package
* Save and Build:

# Click Save and then Build Now to start the build process.

![Screenshot 2025-04-18 195428](https://github.com/user-attachments/assets/fb33f0ac-4e3b-4bcf-bba0-eb2690954638)

# Check the Console Output to confirm that the build was successful.

![Screenshot 2025-04-18 195407](https://github.com/user-attachments/assets/99056f8e-b0c8-4c6c-aa91-f8f120e935b4)


# Conclusion
* By following these steps, you have:
* Created a simple Java project with Maven.
* Configured a Jenkins job to automate the build process using Maven.
* Set up Jenkins to use a local folder on an EC2 instance for the build.

