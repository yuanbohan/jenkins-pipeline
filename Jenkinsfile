pipeline {
    agent any
    environment {
        runtime_env =  'stage'
    }
    stages {
        stage('Example') {
            steps {
	    	sh 'printenv'
                echo 'Hello Jenkins Pipeline Step 1'
                echo 'Hello Jenkins Pipeline Step 2'
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello!'
        }
    }
}