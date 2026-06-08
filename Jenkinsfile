pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp:v1"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/yourusername/myapp.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Build Application') {
            steps {
                sh 'python app.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker rm -f mycontainer || true'
                sh 'docker run -d --name mycontainer $IMAGE_NAME'
            }
        }
    }
}