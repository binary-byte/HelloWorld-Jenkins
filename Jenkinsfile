def properties
def id_address

def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: 'branch-specific.properties'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER}"
        id_address = properties['build_ip_address']
        echo "${id_address}"
        echo "ip address: ${properties.build_ip_address} : ${properties.build_port}"
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