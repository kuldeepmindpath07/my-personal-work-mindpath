pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'I am cloning the three-tier application'
            }
        }
        stage('Clone') {
            steps {
                script {
                    git url: "https://github.com/kuldeepmindpath07/my-personal-work-mindpath.git", branch: "my-files"
                }
                echo "Cloning successful"
            }
        }
        stage('Build Frontend and Backend in Parallel') {
            parallel {
                stage('Build Frontend') {
                    steps {
                        echo 'Building frontend...'
                        dir('frontend') { // Navigate to the frontend directory
                            sh 'docker build -t my-frontend:latest -f Dockerfile .'
                        }
                    }
                }
                stage('Build Backend') {
                    steps {
                        echo 'Building backend...'
                        dir('backend') { // Navigate to the backend directory
                            sh 'docker build -t my-backend:latest -f Dockerfile .'
                        }
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'docker-compose down && docker-compose up -d'
            }
        }
        stage('pushing'){
            steps{
                 sh "docker login -u kuldeep433 -p Lala@2003ji"
		         sh "docker image tag three-tier_web:latest kuldeep433/three-tier_web"
		         sh "docker image tag three-tier_api:latest kuldeep433/three-tier_api"    
		         sh "docker push three-tier_web"
                 	 sh "docker push three-tier_api"
            }
        }
    }
}
