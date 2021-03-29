pipeline {
    agent any

    stages {
        stage('Compile Stage') {
            steps {
                maven(maven : 'maven 3.6.3') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Test Stage') {
            steps {
                maven(maven : 'maven 3.6.3') {
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy Stage') {
            steps {
                maven(maven : 'maven 3.6.3') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}