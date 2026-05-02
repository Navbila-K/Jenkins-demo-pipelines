pipeline {
    agent any

    tools {
        maven 'maven3.9.9'
        jdk 'JDK21'
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/Navbila-K/Jenkins-demo-pipelines.git'
            }
        }

        stage('Build and Unit Test') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Checkstyle Analysis') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Now Archiving it...'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
