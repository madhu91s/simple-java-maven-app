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
    stages {
        stage('Build') { 
            steps {
			
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}