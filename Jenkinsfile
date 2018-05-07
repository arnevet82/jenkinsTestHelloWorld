pipeline {
    agent { docker { image 'centos' } }
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











