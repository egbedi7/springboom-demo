pipeline {
    agent any

    stages {

        stage('Build Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t springboot-demo:1.0 .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f springboot-demo || true'
                sh 'docker run -d -p 8080:8080 --name springboot-demo springboot-demo:1.0'
            }
        }
    }
}
