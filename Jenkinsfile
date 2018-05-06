pipeline {
agent { docker { image 'python:2.7.5' } }	 
    stages {
        stage('build') {
            steps {
                echo 'building...'
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















