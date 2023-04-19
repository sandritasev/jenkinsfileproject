pipeline {
    agent any
    environment {
        
        NEXUS_URL = "192.168.0.16:8082"
        
    }
   
    stages {
        stage('Initialize'){
            steps {
	        script {
		    def dockerHome = tool 'mydocker'
                    env.PATH = "${dockerHome}/bin:${env.PATH}"
		}
	    }	
    	}	
	stage('pull nexus repository') {
            steps {                
		
		sh 'docker pull $NEXUS_URL/contenedores/practica-final-master-webapp:1.0'
		
            }
        }
        stage('DEV') {
            steps {
                sh'npm run serve'

            }
        }
        stage('verificarCURLdev') {
            steps {
                
		script {
                    final String url = "http://192.168.0.16:5000"

                    final String response = sh(script: "curl -s $url", returnStdout: true).trim()

                    echo response
                }

            }
        }
	stage('QA') {
            steps {
                
		sh'npm run serve'

            }
        }
	stage('verificarCURLqa') {
            steps {
                
		script {
                    final String url = "http://192.168.0.16:5000"

                    final String response = sh(script: "curl -s $url", returnStdout: true).trim()

                    echo response
                }

            }
        }
	stage('PROD') {
            steps {
                
		sh'npm run serve'


            }
        }
	stage('verificarCURLprod') {
            steps {
                
		script {
                    final String url = "http://192.168.0.16:5000"

                    final String response = sh(script: "curl -s $url", returnStdout: true).trim()

                    echo response
                }

            }
        }
	
    }
}