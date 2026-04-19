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
            bat '"C:\\Users\\abhis\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pip install -r requirements.txt'
            bat '"C:\\Users\\abhis\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pytest'
        }
    }
}
    }
}