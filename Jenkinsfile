pipeline {
    agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                echo 'building...'
                sh 'whoami'
         checkout scm
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











