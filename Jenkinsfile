pipeline {

    	environment {
     
		name = 'jenkinsTestHelloWorld'
           def uploadSpec = """{"files": [{"pattern": "/var/lib/jenkins/workspace/jenkinsTestHelloWorld.tgz","target": "example-repo-local/"]}"""
        
        
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
			  server = Artifactory.server 'art-1'	
			 server.bypassProxy = true
		server.upload spec: uploadSpec
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
