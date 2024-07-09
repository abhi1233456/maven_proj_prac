pipeline {
    agent any
    tools {
        maven 'Maven 3.9.7' 
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/abhi1233456/maven_proj_prac.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Clean and build the Maven project
                    sh 'mvn clean install'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run unit tests
                    sh 'mvn test'
                }
            }
            post {
                always {
                    // Publish test results
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }
}
