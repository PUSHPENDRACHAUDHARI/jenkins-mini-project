pipeline {
    agent any

    environment {
        APP_NAME = "demoapp"
        IMAGE_NAME = "demoapp:latest"
    }

    stages {

        stage("Checkout") {
            steps {
                // For Jenkins "Pipeline script from SCM" this checkout is optional,
                // but keeping it here makes the pipeline usable from "Pipeline script" too.
                checkout scm
            }
        }

        stage("Maven Build") {
            steps {
                sh "mvn clean package -DskipTests"
            }
        }

        stage("Docker Build") {
            steps {
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage("Docker Run") {
            steps {
                sh '''
                docker rm -f ${APP_NAME} || true
                docker run -d --name demoapp -p 9090:8080 demoapp:latest
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment done. App running on port 8080"
        }
        failure {
            echo "❌ Pipeline failed"
        }
    }
}
