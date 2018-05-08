pipeline {
agent { docker { image 'python:2.7.15-alpine3.7' } }
def server = Artifactory.server 'art-1'
    stages {
        stage('build') {
            steps {
                echo 'building...'
                checkout scm
                echo 'Hello Mr. ${server}'
                
            }
        }
  stage('run'){
            steps {
                sh 'python --version'
                sh 'python python_test.py'
            }
        }
    }
}
