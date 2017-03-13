pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello Jenkins Pipeline'
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
        }
    }
}