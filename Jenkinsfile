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
		tar -czvf jenkinsTestHelloWorld.tgz .tar.gz .
                
		//sh "echo ${server}"
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
