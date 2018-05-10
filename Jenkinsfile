pipeline {
environment {
     name = 'jenkinsTestHelloWorld'
     }

agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                 echo 'building...'
                 checkout scm
                 sh 'tar -czvf ${name}.tgz /var/lib/jenkins/workspace/jenkinsTestHelloWorld'
                 script { 
                 def server = Artifactory.server 'art-1'
                 def server = Artifactory.server url: 'http://jenkins:8081/artifactory', username: 'admin', password: 'password'
                 sh "echo ${server}"
                 def uploadSpec = """{
                    "files": [{
                       "pattern": "*test*",
                       "target": "example-repo-local"
                    }]
                 }"""

                 server.upload(uploadSpec) 
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
