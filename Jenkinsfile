pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    environment {
        PYTHON = "C:\\Users\\abhis\\AppData\\Local\\Python\\bin\\python.exe"
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
                    bat '"%PYTHON%" -m pip install -r requirement.txt'
                    bat '"%PYTHON%" -m pytest'
                }
            }
        }

        stage('Build Docker Image - Java') {
            steps {
                dir('Java_app') {
                    bat 'docker build -t abhishekthakare97/java-app:latest .'
                }
            }
        }

        stage('Build Docker Image - Python') {
            steps {
                dir('Python_app') {
                    bat 'docker build -t abhishekthakare97/python-app:latest .'
                }
            }
        }

        stage('Push to DockerHub') {
    steps {
        withCredentials([usernamePassword(
            credentialsId: 'dockerhub-creds',
            usernameVariable: 'DOCKER_USER',
            passwordVariable: 'DOCKER_PASS'
        )]) {

            bat 'echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
            bat 'docker push abhishekthakare97/java-app:latest'
            bat 'docker push abhishekthakare97/python-app:latest'
        }
    }
}
    }
}