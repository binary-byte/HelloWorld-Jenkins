def properties

def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: 'branch-specific.properties'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER} ${properties.application.name}"       
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
                echo "ip address: ${properties.build.ip_address} : ${properties.build.port}"
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing...'
                echo "ip address: ${properties.test.ip_address} : ${properties.test.port}"
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