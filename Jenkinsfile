pipeline {
agent { docker { image '2.7.15-alpine3.6' } }	 
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















