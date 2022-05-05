pipeline {
    agent none

    
    stages {

        stage ('git & build app') {
            agent {
                docker {
                    image 'docker.teq.kz:8888/docker-build:latest'
                    args '-v /war-folder:/var/lib/jenkins/workspace/jenkins_build_in_docker/target'
                }       
            }
            steps {
                git 'https://github.com/Dishair/boxfuse-origin.git'
                sh "mvn package"
            }  
        }



        stage ('Make docker image with app') {
            agent any
            steps {
                sh '''#!/bin/bash
                mkdir -p /build-folder
                cd /build-folder
                mv /var/lib/jenkins/workspace/build-in-docker/target/*.war /build-folder/
                rm -f Dockerfile
                echo 'FROM tomcat:alpine as prod\n' >> /build-folder/Dockerfile
                echo 'COPY hello-1.0.war /usr/local/tomcat/webapps\n' >> /build-folder/Dockerfile
                echo 'EXPOSE 8080\n' >> /build-folder/Dockerfile
                echo 'CMD ['catalina.sh', 'run']\n' >> /build-folder/Dockerfile
                '''
                sh ' docker build -t tomcat-run /build-folder/.'
            }
        }


        stage('Run docker container on server') {
            agent any
            steps {
                sh 'docker run tomcat-run'
            }
        }      

    }
}