pipeline {
    agent any
    tools { 
        maven 'mvn 3.6.2' 
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Deploy') {
        
        	environment {
				ANYPOINT_CREDENTIALS = credentials('anypointPlatform')
			}
            steps {
                sh 'mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Dworkers=1 -Dworker.type=Micro -Denvironment=Sandbox -Dmule.version=4.4.0' -Dapplication.name=dev-hello
            }
        }
    }
}