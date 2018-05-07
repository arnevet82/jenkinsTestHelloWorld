
pipeline {
    agent {
        docker {
            image 'python:2.7.15-alpine3.7'
            args '-u root:sudo -v $home/natalies'
        }
    }
    stages {
        stage('run'){
            steps {
                sh 'python --version'
                sh 'python python_test.py'
            }
        }
    }
}















