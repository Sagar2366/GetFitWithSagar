pipeline {
    agent any 
    stages {
        stage('Verify java is installed or not') { 
            steps {
                sh "java --version"
                sh "whoami"
                
            }
        }
        stage('compile java program') { 
            steps {
                sh 'ls -al'
                sh 'javac Jenkins/HelloWorld.java'
            }
        }
        
        stage('Execute java application') { 
            steps {
                sh 'ls -al'
                sh 'cd Jenkins && java HelloWorld'
            }
        }
    }
}
