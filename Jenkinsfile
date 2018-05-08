pipeline {
environment {
     server = Artifactory.server 'art-1'
     uploadSpec = """{
           "files": [
                         {
                              "pattern": "jenkinsTestHelloWorld/*test*.py",
                              "target": "jenkinsTestHelloWorld-repo/test-files/"
                    }
               ]
          }"""
     }

agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                echo 'building...'
                checkout scm
                sh "echo ${server}"
                server.upload(uploadSpec)
                
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
