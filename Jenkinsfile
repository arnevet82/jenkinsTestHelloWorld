pipeline {
     agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                sh 'ls /var/run'
            }
        }
    }
}
