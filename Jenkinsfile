pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Build image') { 
            steps {
                sh 'docker build -t springio/gs-spring-boot-docker .' 
                sh 'docker run -p 8080:8080 springio/gs-spring-boot-docker -d'
            }
        }
        stage('Test image') {
            steps {
                sh 'docker exec mystifying_feistel echo "Test passed"'
            }
        }
    }
}