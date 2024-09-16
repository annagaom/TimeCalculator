
pipeline {
    agent any
    tools {
        maven 'HomeBrew Maven'
        jdk 'jdk-20'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/annagaom/TimeCalculator.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: 'target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/TEST-TimeCalculatorTest.xml'
            jacoco execPattern: 'target/jacoco.exec'
        }
    }
}

