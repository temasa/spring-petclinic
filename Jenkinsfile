pipeline {
    agent {
        docker {
            label 'slave1'
            image 'maven:3.5-alpine'
        }
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/temasa/spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: "target/*.jar", fingerprint: true
            }
        } 
    }
}
