pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/awspandian/dd-feb.git'
            }
			
        }
		        stage('Build') {
            steps {
                sh 'mvn clean'
				sh 'mvn install'
            }
			
        }
		stage('Build Docker Image') {

            steps {
			   script {
			     app = docker.build("dockerpandian/ddeploy-9am")
				 app.inside {
				   sh 'echo $(curl localhost:8080)'
				            }
                       }	
                  }
		}   
		stage('Push Docker Image') {
		  	when {
			   branch 'master'
			   }
			   steps {
			     script {
				   docker.withRegistry('https://registry.hub.docker.com', 'docker'){
				     app.push("${env.BUILD_NUMBER}")
					 app.push("latest")
				   }
				 }
			   }
		}
		}
}
