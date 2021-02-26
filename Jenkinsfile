pipeline {
agent any
tools {
maven 'maven'
}
stages {
stage('Git Checkout') {
steps {
git branch: 'master',
credentialsId: '0122853b-cb76-47f5-bb46-cc5a3c7649fc',
url: 'https://github.com/jatinkumar0/junit.git'
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
