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
            agent {
                any
            }
            steps {            
                sh "NEWFILE='FROM tomcat:alpine as prod\nCOPY /war-folder /usr/local/tomcat/webapps\nEXPOSE 8080\nCMD ['catalina.sh', 'run']\n'"
                sh 'echo $NEWFILE > /Dockerfile'
                // sh '/usr/bin/docker run hello-world'
                sh "docker build -t tomcat-run /."
            }
        }


        stage('Run docker container on server') {
            steps {
                sh 'docker run tomcat-run'
            }
        }      

    }
}