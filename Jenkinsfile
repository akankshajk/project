
pipeline {
agent {
label {
		label "built-in"
		customWorkspace "/mnt/builtin"
	
		
		}
	
		}
	tools {
			maven 'maven-master' 
			git 'Default'
		}
		stages{
			stage('clone-repo')
			{
				steps{
					git branch: 'master' , url: 'https://github.com/akankshajk/project.git'
				}
			}
		}
	       stages{
	               stage ('CLEAN_OLD_M2') {
		       steps {
				sh "rm -rf /root/.m2/repository"
				
			}
		}
	}
	stages{	
	stage ('MAVEN_BUILD') {
		
			steps {
				sh "mvn clean install"
			}
	             }	
		}
		stages{
		stage ('COPY_WAR_TO_Server'){
		
				steps {
					sh "rm -rf *"	
  	              sh "scp -r //mnt/masterwar/target/LoginWebApp.war akanksha@172.31.41.180:/mnt/server/apache-tomcat-9.0.98/webapps"

						}
				}
		}
	
	
	}

