def properties = null

def loadProperties() {
    node {
        properties = readProperties file: 'branch-specific.properties'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER}"
    }
}

pipeline {
    agent any
    stages {
        stage ('Init') {
            steps {
              loadProperties()
            }
        }

        stage ('Build') {
            steps {
                echo 'Building...'
                echo "ip address: ${properties.build_ip_address}:${properties.build_port}"
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing...'
                echo "ip address: ${properties.test_ip_address}:${properties.test_port}"
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