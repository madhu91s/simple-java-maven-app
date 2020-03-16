pipeline {
    environment {
		HTTP_PROXY="http://172.20.27.231:3128"
		HTTPS_PROXY="http://172.20.27.231:3128"
	}
	agent {
        
		docker {
            args '-v /var/run/docker.sock:/var/run/docker.sock -v /root/.m2:/root/.m2' 
            image 'maven:3-alpine'
        }
		
    }
	tools{
		maven 'Maven 3.3.9'
	}
    stages {
		stage('Initialize'){
		sh '''
			echo "PATH = ${PATH}"
			echo "M2_HOME = ${M2_HOME}"
		'''
		
		}
        stage('Build') { 
            steps {
			
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}