def properties

pipeline {
    agent any
    stages {
        stage ('Init') {
            steps {
                script {
                    properties = readProperties file: 'branch-specific.properties'
                    echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER}"
                }
            }
        }

        stage ('Build') {
            steps {
                echo 'Building...'
                echo "ip address: ${build.ip_address}:${build.port}"
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing...'
                echo "ip address: ${test.ip_address}:${test.port}"
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