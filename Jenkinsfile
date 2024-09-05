pipeline {
    agent any

    tools {
        maven 'Maven 3.8.7-2'  // Ensure this matches the name you used in Global Tool Configuration
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -Dmaven.test.skip=true'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.war'
            }
        }

        stage('Deployment') {
            steps {
                deploy adapters: [
                    tomcat9(
                        url: 'http://192.168.0.112:9050/', 
                        credentialsId: 'tomcatCreds'
                    )
                ], 
                war: 'target/*.war', 
                contextPath: 'app'
            }
        }
    }
}
