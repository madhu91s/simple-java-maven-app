pipeline {
    environment {
		HTTP_PROXY="172.20.27.231:3128"
		HTTPS_PROXY="172.20.27.231:3128"
	}
	agent {
        
		docker {
            image 'maven:3-alpine'
			
            args '-v /root/.m2:/root/.m2' 
        }
		
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}