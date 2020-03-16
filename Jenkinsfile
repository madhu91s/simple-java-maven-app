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
	
		stage('Initialize'){
			steps{
			
				sh '''
					echo "PATH = ${PATH}"
					echo "M2_HOME = ${M2_HOME}"
				'''
			}
		}
        stage('Build') { 
            steps {
				withMaven(globalMavenSettingsConfig: '1e257ac6-8f8f-49dc-ae30-fe8d573c599a') {
					sh 'mvn -B -DskipTests clean package' 
				}
            }
        }
    }
}