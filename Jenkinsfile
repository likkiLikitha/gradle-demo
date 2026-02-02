pipeline {
    agent any

    tools {
        jdk 'JDK'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/likkiLikitha/gradle-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    ./gradlew sonarqube \
                    -Dsonar.projectKey=gradle-demo \
                    -Dsonar.projectName=gradle-demo \
                    -Dsonar.coverage.jacoco.xmlReportPaths=build/reports/jacoco/test/jacocoTestReport.xml
                    '''
                }
            }
        }
    }
}
