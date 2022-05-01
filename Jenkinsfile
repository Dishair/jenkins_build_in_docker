pipeline {
    agent {

        docker {
            image 'devcvs-srv01:5000/shop2-backend/jenkins-agent'
        }
    }

    tools {
        maven "m3"
    }
    
    stages {
        stage ('git') {
            steps {
                git 'https://github.com/Dishair/boxfuse-origin.git'    
            }  
        }


        stage ('build') {
            steps {
                sh 'mvn package'    
            } 
        }


        stage ('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '17d1030d-ccb2-472e-9a9d-0b98edccc00f', path: '', url: 'http://192.168.56.21:8080')], contextPath: 'mywebapp3', war: '**/*.war'    
            } 
        }

    }
}