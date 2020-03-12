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
				sh 'mvn clean install -DproxySet=true -DproxyHost=proxy5.ads.stba.de -DproxyPort=8080'
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}