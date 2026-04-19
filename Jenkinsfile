pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    stages {
        stage('Build Java') {
            steps {
                dir('Java_app') {
                    bat 'mvn clean package'
                }
            }
        }

        stage('Test Java') {
            steps {
                dir('Java_app') {
                    bat 'mvn test'
                }
            }
        }

        stage('Test Python') {
    steps {
        dir('Python_app') {
            bat 'python -m pip install -r requirements.txt'
            bat 'python -m pytest'
        }
    }
    }
    }
}