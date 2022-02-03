pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/awspandian/dd-feb.git'
            }
		stage('Build') {
            steps {
                sh 'mvn clean'
				sh 'mvn install'
            }	
        }
    }
}
}
