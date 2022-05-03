pipeline {
    agent {

        docker {
            image 'docker.teq.kz:8888/docker-build'
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
                touch Dockerfile
                echo 'FROM tomcat:alpine as prod' >> Dockerfile
                echo 'VOLUME /boxfuse-origin/target /usr/local/tomcat/webapps' >> Dockerfile
                echo 'EXPOSE 8080' >> Dockerfile
                echo 'CMD ["catalina.sh", "run"]' >> Dockerfile
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