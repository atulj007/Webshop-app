pipeline {
    agent any
    
    tools {
        jdk 'jdk17'
    }
    environment {
        
        SCANNER_HOME= tool 'sonar-scanner'
    }
    

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/atulj007/Webshop-app.git'
            }
        }
        
         stage('Sonarqube') {
            steps {
             withSonarQubeEnv('sonar') {
             sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=webshop \
              -Dsonar.projectName=Webshop-App'''
              }   
                
            }
        }
        
         stage('Build and Deploy') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}
