pipeline {
    agent any

    stages {
        stage('Compile') {
            steps{
                sh 'mvn clean compile -e'
            }
        }
        stage('Test') {
            steps{
                sh 'mvn clean test -e'
            }
        }
        stage('Package') {
            steps{
                sh 'mvn clean package -e'
            }
        }
        stage('SonarQube analysis') {
		    withSonarQubeEnv(installationName: 'sonar') {
		    	sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
		    }
		}
        stage('Run') {
            steps{
                sh 'mvn spring-boot:run &'
            }
        }
        stage('Curl') {
            steps{
                sh 'sleep 20'
                sh 'curl -X GET "http://localhost:8888/rest/mscovid/test?msg=testing"'
            }
        }
    }
}
