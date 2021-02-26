pipeline {
agent any
tools {
maven 'maven'
}
stages {
stage('Git Checkout') {
steps {
git branch: 'main',
credentialsId: 'e8d0d800-ea2d-43eb-a937-ab0a484cace8',
url: 'https://github.com/navneetguraya/new.git'
}
}
stage ('Clean') {
steps {
sh 'mvn clean'
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
post {
always {
junit '**/target/surefire-reports/*.xml'
}
}
}
stage ('Package') { 
steps {
sh 'mvn package'
}
}
stage ('Deploy War File') {
steps {
sh "cp /root/.jenkins/workspace/navneet/gameoflife-web/target/gameoflife.war /etc/apache-tomcat-8.5.61/webapps/"
}
}
}
}
