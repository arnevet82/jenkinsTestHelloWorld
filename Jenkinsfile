pipeline {
    agent { docker { image 'python:2.7.15-alpine3.7' } }
    stages {
        stage('build') {
            
	steps {
                
		echo 'building...'
               
		checkout scm
                
		sh "echo ${server}"
                
		
           
           }
      
	  }

        stage('Artifactory download and upload'){
            steps {
                script{
                    // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                    def server = Artifactory.server 'art-1'

                    // Read the download and upload specs:
                    // def downloadSpec = readFile 'jenkinsTestHelloWorld/python_test.py'
                    def uploadSpec = readFile 'jenkinsTestHelloWorld/python_test.py'

                    // Download files from Artifactory:
                    // def buildInfo1 = server.download spec: downloadSpec
                    // Upload files to Artifactory:
                    def buildInfo2 = server.upload spec: uploadSpec

                    // Merge the local download and upload build-info instances:
                    // buildInfo1.append buildInfo2

                    // Publish the merged build-info to Artifactory
                    server.publishBuildInfo buildInfo2
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
