pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                git url: 'file:///opt/git/myproject.git', branch: 'master'
            }
        }

        stage('Build Docker') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Deploy Docker') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
