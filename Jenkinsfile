pipeline {
    agent any 

    environment {
        
        DOCKER_HUB_USERNAME = 'dockerHubCred’
        DOCKER_HUB_PASSWORD = credentials('dockerHubCred')  

    }

    stages {
        stage('Checkout Code') {
            steps {
               
                git branch: 'main', url: 'https://github.com/Sejalthakur17/fusionpact-devops-challenge.git'
            }
        }

        stage('Install Dependencies and Run Tests') {
            steps {
                
                dir('backend') {
                    sh 'pip install -r requirements.txt'  // Install Python dependencies
                    sh 'pytest'  // Run unit tests; ensure pytest is in requirements.txt
                }
          
            }
            post {
                failure {
                    error 'Tests failed; stopping the pipeline.'
                }
            }
        }

        stage('Build Docker Images') {
            steps {
               
                sh 'docker build -t Sejalthakur/frontend:latest ./frontend'
                
        
                sh 'docker build -t Sejalthakur/backend:latest ./backend'
            }
        }

        stage('Push Docker Images to Registry') {
            steps {
                
                sh 'echo $DOCKER_HUB_PASSWORD | docker login -u $DOCKER_HUB_USERNAME --password-stdin'
                
              
                sh 'docker push Sejalthakur/frontend:latest'
                sh 'docker push Sejalthakur/backend:latest'
            }
            post {
                failure {
                    echo 'Failed to push images; check Docker credentials.'
                }
            }
        }

        stage('Deploy ') {
            steps {
                
                
      
                sh "docker-compose down && docker-compose up -d"
            }
            post {
                success {
                    echo 'Deployment successful! Check your cloud console.'
                }
                failure {
                    echo 'Deployment failed; verify cloud credentials and resources.'
                }
            }
        }
    }

    post {
    always {
       
        sh 'docker system prune -f'
        echo 'Pipeline completed.'
    }
    success {
        
        mail to: 'sejalthakur016@gmail.com', subject: 'Pipeline Succeeded', body: 'Your app has been deployed successfully.'
    }
    failure {
        mail to: ‘sejalthakur016@gmail.com’ subject: 'Pipeline Failed', body: 'Check Jenkins logs for details.'
    }
}
