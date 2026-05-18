pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'dev',
                url: 'https://github.com/acemilyalcin/sample-node-project.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t node-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f node-container || true'
                sh 'docker run -d -p 3000:3000 --name node-container node-app'
            }
        }

        stage('Test App') {
            steps {
                sh 'curl http://localhost:3000'
            }
        }
    }
}

