pipeline {
	agent docker
	
  environment {
    
    artifactId = readMavenPom().getArtifactId()
    version = readMavenPom().getVersion()
    Nexus_Cred = credentials('nexus-cred')
  }	
  
	stages {
			
		stage ('Git Checkout')  {
				steps {
					git branch: 'dev',
					
					url: "https://github.com/birendersingh03/java_project.git"

        }
			}
			
		stage ('Build') {
		
			agent {
                docker {
                         reuseNode true
                         image 'maven'
						}
			steps {
			
			    sh 'mkdir -p ${WORKSPACE}'
				sh 'cp -r ${WORKSPACE}/* ${WORKSPACE} '
				sh 'cd ${WORKSPACE}/src/main/java'
				sh 'mvn clean install'		
			}
		}
	
	
	
		
	}
}
