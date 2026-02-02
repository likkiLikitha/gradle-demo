pipeline {
    agent any

    tools {
        jdk 'JDK21'
        gradle 'Gradle'
    }

    stages {

        stage('Build') {
            steps {
                bat 'gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                bat 'gradlew test'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat 'gradlew sonar'
                }
            }
        }
    }
}
