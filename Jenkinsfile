#!groovy

pipeline {

  agent any

  environment {
    DB_NAME      = 'test'
    DB_USENAME   = 'root'
    DB_PWD       = 'root'
    PR_MD_URL    = "[#${env.ghprbPullId} ${env.ghprbPullTitle}](https://github.com/${env.ghprbGhRepository}/pull/${env.ghprbPullId})"
    LOG_MD_URL   = "click [ci log](${env.JOB_DISPLAY_URL}) to see detail."
  }

  stages {

    stage('Prepare Schema') {
      steps {
        // sh 'printenv'
        sh "echo 'do some preparation'"
      }
    }

    stage('Clean') {
      steps {
        sh 'lein clean' // this is for Clojure Project, you can change to your language stack
      }
    }

    stage('Test') {
      steps {
        retry (3) {
          timeout(time: 5, unit: 'MINUTES') {
            sh 'lein test' // this is for Clojure Project, you can change to your language stack
          }
        }
      }
    }
  }

  post {
    success {
      bearychatSend message: "${env.ghprbPullAuthorLoginMention} **Success** for PR ${PR_MD_URL}",
                    color: '#0000FF',
                    attachmentText: "${env.LOG_MD_URL}"
    }
    failure {
      bearychatSend message: "${env.ghprbPullAuthorLoginMention} **Failure** for PR ${PR_MD_URL}",
                    color: '#FF0000',
                    attachmentText: "${env.LOG_MD_URL}"
    }
    unstable {
      bearychatSend message: "${env.ghprbPullAuthorLoginMention} **Unstable** for PR ${PR_MD_URL}",
                    color: '#808080',
                    attachmentText: "${env.LOG_MD_URL}"
    }
    aborted {
      bearychatSend message: "${env.ghprbPullAuthorLoginMention} **Aborted** for PR ${PR_MD_URL}",
                    color: '#000000',
                    attachmentText: "${env.LOG_MD_URL}"
    }
  }
}
