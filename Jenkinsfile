pipeline {
    agent any

    environment {
        IMAGE_NAME   = "devops-portfolio"
        AWS_REGION   = "eu-west-33"
        ECR_REGISTRY = "106300404586.dkr.ecr.eu-west-3.amazonaws.com"
        ECR_REPO     = "devops-portfolio"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                sh '''
                pwd
                ls -lrt
                '''
            }
        }

        stage('SonarQube Scan') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner'

                    withSonarQubeEnv('sonarqube') {
                        sh """
                        ${scannerHome}/bin/sonar-scanner
                        """
                    }
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh """
                docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} .
                """
            }
        }

        stage('Login to Amazon ECR') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'aws-creds',
                        usernameVariable: 'AWS_ACCESS_KEY_ID',
                        passwordVariable: 'AWS_SECRET_ACCESS_KEY'
                    )
                ]) {

                    sh """
                    aws ecr get-login-password --region ${AWS_REGION} | \
                    docker login --username AWS --password-stdin ${ECR_REGISTRY}
                    """
                }
            }
        }

        stage('Tag Docker Image') {
            steps {
                sh """
                docker tag ${IMAGE_NAME}:${BUILD_NUMBER} ${ECR_REGISTRY}/${ECR_REPO}:${BUILD_NUMBER}
                """
            }
        }

        stage('Push Docker Image') {
            steps {
                sh """
                docker push ${ECR_REGISTRY}/${ECR_REPO}:${BUILD_NUMBER}
                """
            }
        }

        stage('Verify Image in ECR') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'aws-creds',
                        usernameVariable: 'AWS_ACCESS_KEY_ID',
                        passwordVariable: 'AWS_SECRET_ACCESS_KEY'
                    )
                ]) {

                    sh """
                    aws ecr describe-images \
                    --repository-name ${ECR_REPO} \
                    --region ${AWS_REGION}
                    """
                }
            }
        }
    }

    post {

        success {
            echo 'Pipeline Completed Successfully!'
        }

        failure {
            echo 'Pipeline Failed!'
        }

        always {
            cleanWs()
        }
    }
}