pipeline {
agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                echo 'building...'
                checkout scm
                def server = Artifactory.server 'art-1'
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
