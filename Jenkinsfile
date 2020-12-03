pipeline {
    agent any

    stages {
        stage('Compile') {
            steps{
                dir('C:\\Proyectos\\ejemplo-maven'){
                    sh 'mvn clean compile -e'
                }
            }
        }
        stage('Test') {
            steps{
                dir('C:\\Proyectos\\ejemplo-maven'){
                    sh 'mvn clean test -e'
                }
            }
        }
        stage('Package') {
            steps{
                dir('C:\\Proyectos\\ejemplo-maven'){
                    sh 'mvn clean package -e'
                }
            }
        }
        stage('Run') {
            steps{
                dir('C:\\Proyectos\\ejemplo-maven'){
                    sh 'mvn spring-boot:run &'
                }
            }
        }
        stage('Curl') {
            steps{
                dir('C:\\Proyectos\\ejemplo-maven'){
                    sh 'sleep 20'
                    sh 'curl -X GET "http://localhost:8082/rest/mscovid/test?msg=testing"'
                }
            }
        }
    }
}
