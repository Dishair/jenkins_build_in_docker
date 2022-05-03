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
                sh "tee Dockerfile <<EOF
                FROM tomcat:alpine as prod
                COPY /var/lib/jenkins/workspace/jenkins_build_in_docker/target /usr/local/tomcat/webapps
                EXPOSE 8080
                CMD ['catalina.sh', 'run']
                EOF"
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