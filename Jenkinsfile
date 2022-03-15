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
    				withSonarQubeEnv() {
      					sh "${scannerHome}/bin/sonar-scanner"
				}
				//sh "${mvnHome}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Sample:7899756022"
			    }
			}		    
		}
	}
}
