def properties

def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: 'branch-specific.properties'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER}"

        id_address = properties['build_ip_address']
        echo "${id_address}"
        echo "ip address: ${properties.build.ip_address} : ${properties.build.port}"
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