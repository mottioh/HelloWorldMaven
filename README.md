Installed Centos Machine on VirualBox

Installed Docker - $ sudo yum install -y yum-utils

$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
sudo yum install docker-ce docker-ce-cli containerd.io

Pulled Jenkins Container -docker pull jenkins/jenkins

Installed Maven within the container -  sudo docker exec -u root -t -i [container-id]  bash

sudo apt update

sudo apt install maven

Install git Plugin

Install Maven Plugin

Install Clean Workspace Plugin

Created new Maven project

Task requests:
Check out from fork: 

Declarative automatically performs a checkout of source code on the agent, we  use it in the JenkinsfileUnix file - the source of it:

https://www.jenkins.io/blog/2017/02/07/declarative-maven-project/

deleted the Deploy section from the code as requested :

        stage('Deploy') {
            steps {
               withMaven(maven : 'apache-maven-3.3.3'){
                        sh "mvn deploy"
                        
 the JenkinsfileUnix code is now : 
 
 pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                withMaven(maven : 'apache-maven-3.3.3'){
                        sh "mvn clean compile"
                }
            }
        }
        stage('Test'){
            steps {
                withMaven(maven : 'apache-maven-3.3.3'){
                        sh "mvn test"
                }

            }
        }
    }
}

Clean workspace after successfull run With Clean Workspace plugin       
as shawn in https://github.com/mottioh/HelloWorldMaven/blob/master/Clear_workspace.JPG                     
and in the mail reply that I have sent
