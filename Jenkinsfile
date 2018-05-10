pipeline {
environment {
     server = Artifactory.server 'art-1'
     name = 'jenkinsTestHelloWorld'
     uploadSpec = readFile '/var/lib/jenkins/workspace/jenkinsTestHelloWorld/python_test.py'
     }

agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                echo 'building...'
                checkout scm
                sh "echo ${server}"
                sh 'tar -czvf ${name}.tgz /var/lib/jenkins/workspace/jenkinsTestHelloWorld'
                 script{
                      server.upload("hello")
                 }
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
