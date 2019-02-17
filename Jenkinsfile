pipeline {
    agent {
        docker {
            image 'node:10-alpine'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'yarn'
            }
        }
        stage('Test') {
            steps {
                sh 'yarn test'
            }
        }
    }
    post {
        success {
            slackSend color: 'good', message: "<${env.BUILD_URL}|All tests passed in Jenkis>"
        }
        failure {
            slackSend color: 'danger', message: "<${env.BUILD_URL}|Some of the tests failed in Jenkins>"
        }
    }
}
