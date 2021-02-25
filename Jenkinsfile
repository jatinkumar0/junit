pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main',
                credentialsId: '0122853b-cb76-47f5-bb46-cc5a3c7649fc',
                url: 'https://github.com/jatinkumar0/junit.git'
                }
        }
        stage ('Compile') {
            steps {
                sh 'mvn compile'
                }
            }   
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
        stage ('Creat War File') {
            steps {
                sh 'jar -cf target/*.jar target/*.war'
                }
            }
            stage ('Deploy War File') {
            steps {
                sh "cp target/*.war /etc/apache-tomcat-8.5.61/webapps/"
            }
        }
    }
}
