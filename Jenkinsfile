pipeline {
    agent {

        docker {
            image 'docker-build'
        }
    }

    
    stages {
        stage ('git') {
            steps {
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
                sh 'docker build -t maven-run .'

            }
        }


        stage('Run docker container on server') {
            steps {
                sh 'ssh-keyscan -H devbe-srv01 >> ~/.ssh/known_hosts'
                sh '''ssh jenkins@devbe-srv01 << EOF
                sudo docker pull devcvs-srv01:5000/shop2-backend/gateway-api:2-staging
                cd /etc/shop/docker
                sudo docker-compose up -d
                EOF'''
            }
        }      

    }
}