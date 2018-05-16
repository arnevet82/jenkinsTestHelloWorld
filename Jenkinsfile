pipeline {
environment {
     name = 'jenkinsTestHelloWorld'
     }

    agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            steps {
                 echo 'building...'
                 
                 checkout([
            $class: 'GitSCM',
            branches: [[name: '*/dev']], 
            extensions: [], 
            userRemoteConfigs: [[credentialsId: 'd6564d07-a13c-4477-a5e3-734017e4d590', url: 'https://github.com/arnevet82/jenkinsTestHelloWorld.git']]
                 ])
                 
                 sh 'tar -czvf ${name}.tgz /var/lib/jenkins/workspace/jenkinsTestHelloWorld'
                 script { 
                 def server = Artifactory.newServer url:'http://jenkins:8081/artifactory', username: 'admin', password: 'password'
                 sh "echo ${server}"
                 def uploadSpec = """{
                    "files": [{
                       "pattern": "**.tgz",
                       "target": "condensed-files-local"
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
