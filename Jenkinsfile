def fileProperties
def jsonProperties

def loadProperties() {
    node {
        checkout scm
        fileProperties = readProperties file: 'branch-specific.properties'
        jsonProperties = readJSON file: 'branch-specific.properties'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER}"

        id_address = fileProperties['build.ip_address']
        echo "${id_address}"
        echo "ip address: ${jsonProperties.build.ip_address} : ${jsonProperties.build.port}"
    }
}

pipeline {
    agent any
    stages {
        stage ('Setup') {
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
            cleanWs()
        } 
        success {
            echo 'Pipeline was successful...'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}