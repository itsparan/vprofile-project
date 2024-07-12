pipeline {
    
	agent any
	
	tools {
        maven "maven3"
		jdk  "OracleJDK8"
    }
	
  
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

	

	}
	}
