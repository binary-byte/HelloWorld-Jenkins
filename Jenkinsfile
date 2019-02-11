def properties

def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: 'branch-specific.properties'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER} ${properties.application_name}"
        echo "ip address: ${properties.test_ip_address} : ${properties.test_port}"       
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
        } 
        success {
            echo 'Pipeline was successful...'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}