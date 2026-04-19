pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/AbhishekMThakare/Java-Python-Devops-Project.git'
            }
        }

        stage('Build Java') {
            steps {
                dir('java-app') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Test Java') {
            steps {
                dir('java-app') {
                    sh 'mvn test'
                }
            }
        }

        stage('Test Python') {
            steps {
                dir('python-app') {
                    sh 'pip install -r requirements.txt'
                    sh 'pytest'
                }
            }
        }
    }
}