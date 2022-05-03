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


        stage ('build app & Make docker image with app') {
            steps {
                sh "mvn package"
                sh "touch Dockerfile"
                sh "echo 'FROM tomcat:alpine as prod' >> Dockerfile"
                sh "echo 'COPY /var/lib/jenkins/workspace/jenkins_build_in_docker/target /usr/local/tomcat/webapps' >> Dockerfile"
                sh "echo 'EXPOSE 8080' >> Dockerfile"
                sh 'echo 'CMD ["catalina.sh", "run"]' >> Dockerfile'
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