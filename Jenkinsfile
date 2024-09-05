pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'  // Ensure this matches the name you used in Global Tool Configuration
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
                        credentialsId: 'TomcatCreds'
                    )
                ], 
                war: 'target/*.war', 
                contextPath: 'app'
            }
        }

        stage('Notification') {
            steps {
                emailext(
                    subject: "Job Completed",
                    body: "Jenkins pipeline job for Maven build job completed",
                    to: "ramesh.dadi@xploria.in"
                )
            }
        }
    }
}
pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  // Ensure this matches the name you used in Global Tool Configuration
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
                        credentialsId: 'TomcatCreds'
                    )
                ], 
                war: 'target/*.war', 
                contextPath: 'app'
            }
        }

        stage('Notification') {
            steps {
                emailext(
                    subject: "Job Completed",
                    body: "Jenkins pipeline job for Maven build job completed",
                    to: "ramesh.dadi@xploria.in"
                )
            }
        }
    }
}
