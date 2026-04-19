pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    stages {
        stage('Build Java') {
            steps {
                dir('java-app') {
                    bat 'mvn clean package'
                }
            }
        }

        stage('Test Java') {
            steps {
                dir('java-app') {
                    bat 'mvn test'
                }
            }
        }

        stage('Test Python') {
            steps {
                dir('python-app') {
                    bat 'pip install -r requirements.txt'
                    bat 'pytest'
                }
            }
        }
    }
}