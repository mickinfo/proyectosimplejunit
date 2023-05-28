pipeline {
    agent any
    tools { 
        maven 'mavenjenkins' 
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mickinfo/proyectosimplejunit.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    }
}
