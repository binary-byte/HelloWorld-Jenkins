def fileProperties
def ymalProperties

def loadProperties() {
    node {
        checkout scm
        fileProperties = readProperties file: 'branch-specific.properties'
        ymalProperties = readYaml file: 'branch-specific.yaml'
        echo "Setting up build ${JOB_NAME} # ${BUILD_NUMBER}"

        id_address = fileProperties['build.ip_address']
        echo 'reading file...'
        echo "${id_address}"
        echo 'reading ymal...'
        echo "ip address: ${ymalProperties.env.build.ip_address} : ${ymalProperties.env.build.port}"
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