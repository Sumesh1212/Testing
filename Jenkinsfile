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
			    def mvnHome = tool 'jenkins'
			    withSonarQubeEnv('jenkins') {

				sh "${mvnHome}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Sample:7899756022"
			    }
			}
		    }
		}
	}
}
