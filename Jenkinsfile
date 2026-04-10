pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                script {
                    // Use a workspace clone to avoid local checkout security warning
                    sh '''
                        rm -rf my_project
                        git clone /opt/git/myproject.git my_project
                        cd my_project
                    '''
                }
            }
        }

        stage('Build Docker') {
            steps {
                dir('my_project') {
                    sh 'docker-compose build'
                }
            }
        }

        stage('Deploy Docker') {
            steps {
                dir('my_project') {
                    sh 'docker-compose up -d'
                }
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