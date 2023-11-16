pipeline {
    agent any

    stages {
     stage('ContinuousDownload')
        {
            steps
            {
                git branch: 'zoheb', credentialsId: '{AQAAABAAAAAwUOc1kr0Msj0LPN+NkU/0xUoLYd0dimeg/vwP7SjtC01F8ucZLl7l26IBeD32flaCSZ7xkg+pUf6uWfWHMWQ/WA==}', url: 'https://github.com/phaniapt/jenkins-task.git'
            }
        }
        stage('AddMvn'){
            steps{
                sh 'export M2_HOME=/opt/apache-maven-3.6.3'
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
