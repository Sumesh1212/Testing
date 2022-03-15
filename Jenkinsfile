pipeline {
	agent any
	stages{
		stage ('Git Install') {
			steps{				
				checkout changelog: false, 
					poll: false, 
					scm: [$class: 'GitSCM', branches: [[name: 'master']], extensions: [], 
					      userRemoteConfigs: [[credentialsId: 'Github',url: 'https://github.com/Sumesh1212/jenkins-example.git']]];
			}
		}			
		stage('Sonar scan execution') {
		    // Run the sonar scan
		    steps {
			script {			    
				def scannerHome = tool 'jenkins';
    				withSonarQubeEnv('maven 3.8.4') {
      					sh "${scannerHome}/bin/sonar-scanner"
					/*sh "${scannerHome}/bin/sonar-scanner
					-Dsonar.projectKey=jenkins \ 					
					-Dsonar.host.url=http://localhost:9000 \
					-Dsonar.login=5b1583ae87b2c535ff27fcce6dd671dc6c80e3a9"*/
					//sh "${scannerHome}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=jenkins"
				}
				
			    }
			}		    
		}
	}
}
