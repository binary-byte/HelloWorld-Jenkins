pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage ('Deployment') {
            steps {
                echo 'Deploying...'
            }
        }
    }
    post {
        always {
            echo 'Pipeline has finished!'
        } 
        success {
            echo 'Pipeline was successful...'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}