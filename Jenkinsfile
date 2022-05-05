pipeline {
    agent {

        docker {
            image 'docker.teq.kz:8888/docker-build:latest'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    
    stages {
        stage ('git') {
            steps {
                git 'https://github.com/Dishair/boxfuse-origin.git'
            }  
        }


        stage ('build app & Make docker image with app') {
            steps {            
                sh "mvn package"
                sh "NEWFILE='FROM tomcat:alpine as prod\nVOLUME /boxfuse-origin/target/target /usr/local/tomcat/webapps\nEXPOSE 8080\nCMD ['catalina.sh', 'run']\n'"
                sh 'echo -e $NEWFILE > Dockerfile'
                // sh '/usr/bin/docker run hello-world'
                sh "docker build -t tomcat-run ."
            }
        }


        stage('Run docker container on server') {
            steps {
                sh 'docker run tomcat-run'
            }
        }      

    }
}