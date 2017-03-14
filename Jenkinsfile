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
            bearychatSend (channel: '太阳城-内部', color: '#FFFF00', message: "STARTED: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}](${env.BUILD_URL})")
        }
    }
}