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
  	
	stage('run'){
            
		steps {
                
			sh 'python --version'
                
			sh 'python python_test.py'
           
	}
       
         }
    }
}
