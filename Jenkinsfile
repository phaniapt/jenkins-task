pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'AQAAABAAAAAwNzNPEf8cV+GsSoXnTYOqiE5FDEcL8CQKhvOTqjcO0va9UfnZtkUE97PW7Ihc+OjcoY9wDxYyNrlmzWeXSVtYig==', url: 'https://github.com/phaniapt/jenkins-task.git'
            }
        }
        stage('AddMvn'){
            steps{
                sh 'export M2_HOME=/opt/apache-maven-3.9.2'
                sh 'export M2=$M2_HOME/bin'
                sh 'export PATH=$PATH:$M2'
            }
        }
        stage('CheckVersion'){
            steps{
                sh 'mvn --version'
            }
        }
        stage('Clean'){
            steps{
                sh 'mvn clean'
            }
        }
        stage('Validate'){
            steps{
                sh 'mvn validate'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn package -DskipTests'    
            }
        }
        stage('Deploy'){
            steps{
                sh 'mvn deploy -DskipTests'
            }
        }
    }
}
