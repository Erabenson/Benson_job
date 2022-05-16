pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Erabenson/Benson_job.git'
            }
        }
        stage('Mavin Build') {
            steps {
                sh 'cd MyWebApp && mvn clean package'
            }
        }
        stage('Deploy To Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'b319e482-3227-4765-b8d3-789f8a5bdaa3', path: '', url: 'http://54.193.140.96:8080/')], contextPath: 'benapp', onFailure: false, war: '**/*.war'
            }
        }
        stage('Job Completed') {
            steps {
                echo 'The Job was Successful'
            }
        }
    }
}

