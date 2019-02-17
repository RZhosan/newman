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
            slackSend color: 'good', message: 'All tests passed in Jenkis'
        }
        failure {
            slackSend color: 'bad', message: 'Some of the tests failed in Jenkins'
        }
    }
}
