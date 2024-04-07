pipeline {  
    agent any  
    stages {  
        stage("git_checkout") {  
            steps {  
                echo "cloning repository" 
                echo "repo cloned successfully"  
            }  
        }
        stage('Checkout') {
            steps {
                sh 'echo passed'
                git branch: 'master', url: 'https://github.com/shashirajraja/onlinebookstore.git'
            }
        }
        stage('Build and Test') {
            steps {
                sh 'ls -ltr'
                // build the project and create a JAR file
                sh 'mvn clean package'
            }
        }
        stage('Static Code Analysis') {
            environment {
                SONAR_URL = "http://40.86.186.123:9000/"
            }
            steps {
                sh "mvn clean verify sonar:sonar -Dsonar.projectKey='demo' -Dsonar.host.url='${SONAR_URL}' -Dsonar.login=sqp_25cc2a8d230eabbb45e4999cd89e710023ac3e54"
            }
        }
    }
}
