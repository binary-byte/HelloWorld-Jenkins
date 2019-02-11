pipeline {
    agent any
    stages {
        stage ('Example') {
            steps {
                echo 'Hello World'
            }
        }
    }
    post {
        always {
            echo 'Pipeline has finished!'
        }
    }
}