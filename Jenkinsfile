pipeline {

    	agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            
	steps {
                
		echo 'building...'
               
		checkout scm
                
		//sh "echo ${server}"
           }
      
	  }
  	stage('Artifactory download and upload'){
		steps {
                
		script{
			def server = Artifactory.server 'art-1'
			def uploadSpec = """{
				  "files": [
				    {
				      "pattern": "*test*.py",
				      "target": "python-test-repo/py-files"
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
