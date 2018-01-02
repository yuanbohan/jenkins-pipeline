#!groovy

pipeline {
  agent any
  environment {
    runtime_env = 'test'
  }

  stages {
    stage('test') {
      steps {
        sh 'printenv'
        sh './scripts/hello.sh'
      }
    }
  }

  post {
    always {
      echo 'I will always say Hello!'
    }
  }
}