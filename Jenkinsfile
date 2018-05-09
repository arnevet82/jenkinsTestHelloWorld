pipeline {

    	
	environment {
	server = Artifactory.server 'art-1'	
     	name = 'jenkinsTestHelloWorld'
     	}
	//agent { docker { image 'python:2.7.15-alpine3.7' } }
	agent any
    stages {
        stage('build') {
            
	steps {
                
		echo 'building...'
		checkout scm
		sh 'tar -czvf ${name}.tgz /var/lib/jenkins/workspace/jenkinsTestHelloWorld'
		
		script{
			def uploadSpec = """{
			  "files": [
			    {
			      "pattern": "test.*",
			      "target": "test-repo/python-files/"
			    }
			 ]
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
