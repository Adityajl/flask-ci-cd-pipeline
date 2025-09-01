pipeline {
    agent any

    stages {
        stage('Build & Test') {
            steps {
                echo 'Building and testing the application...'
                sh 'pip install -r requirements.txt'
                sh 'python -m unittest test.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def image = docker.build("aj5400/flask-app:${env.BUILD_NUMBER}")
                    image.push()
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying to Staging Environment..."
                // A real-world deployment command would go here
                echo "ssh user@staging-server 'docker run -d --rm --name staging_app -p 8080:5000 your-docker-hub-username/flask-app:${env.BUILD_NUMBER}'"
            }
        }

        stage('Manual Approval for Production') {
            steps {
                timeout(time: 15, unit: 'MINUTES') {
                    input "Approve deployment to Production? (Review Staging environment first)"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying to Production Environment..."
                // A real-world production deployment command
                echo "ssh user@production-server 'docker run -d --rm --name production_app -p 80:5000 your-docker-hub-username/flask-app:${env.BUILD_NUMBER}'"
            }
        }
    }
}