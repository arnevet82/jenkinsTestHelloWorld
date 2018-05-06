peline {
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















