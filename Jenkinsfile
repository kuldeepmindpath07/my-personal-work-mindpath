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
                            sh 'docker build -t three-tier_web:latest -f Dockerfile .'
                        }
                    }
                }
                stage('Build Backend') {
                    steps {
                        echo 'Building backend...'
                        dir('backend') { // Navigate to the backend directory
                            sh 'docker build -t three-tier_api:latest -f Dockerfile .'
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
        stage('Push to Docker Hub') {
            steps {
               withCredentials([usernamePassword(
                    credentialsId:"demo",
                    usernameVariable:"dockerHubUser", 
                    passwordVariable:"dockerHubPass")]){
                    sh "docker login -u kuldeep433 -p ${env.dockerHubPass}"

                    // Tag and push the frontend image
                    sh "docker tag three-tier_web:latest kuldeep433/three-tier_web"
                    sh "docker push kuldeep433/three-tier_web"

                    // Tag and push the backend image
                    sh "docker tag three-tier_api:latest kuldeep433/three-tier_api"
                    sh "docker push kuldeep433/three-tier_api"
                }
            }
        }
    }
}
