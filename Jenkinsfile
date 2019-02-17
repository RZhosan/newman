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
            slackSend color: 'good', message: "All tests passed in <${env.BUILD_URL}|Jenkis>"
        }
        failure {
            slackSend color: 'danger', message: "Some of the tests failed in <${env.BUILD_URL}|Jenkins>"
        }
    }
}
