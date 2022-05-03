pipeline {
    agent {

        docker {
            image 'docker.teq.kz:8888/docker-build'
        }
    }

    
    stages {
        stage ('git') {
            steps {
                sh 'cd /root/'
                git 'https://github.com/Dishair/boxfuse-origin.git'
            }  
        }


        stage ('build app') {
            steps {
                sh 'mvn package'
                
            } 
        }


        stage('Make docker image with app') {
            steps {
                sh 'cd /root/'
                git 'https://github.com/Dishair/jenkins_build_in_docker.git'
                sh 'cd /root/jenkins_build_in_docker/run'
                sh 'docker build -t tomcat-run .'

            }
        }


        stage('Run docker container on server') {
            steps {
                sh 'docker run tomcat-run'
            }
        }      

    }
}