
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'i am clonning the three tier application'
            }
        }
        stage('clone'){
            steps{
                script{
		    git url: "https://github.com/kuldeepmindpath07/my-personal-work-mindpath.git", branch: "my-files"
		}
                echo "clonning successfull"
            }
        }
	stage('Build Frontend and Backend in Parallel') {
            parallel {
                stage('Build Frontend') {
                    steps {
                        echo 'Building frontend...'
                        sh 'docker build -t my-frontend:latest -f frontend/Dockerfile .'
                    }
                }
                stage('Build Backend') {
                    steps {
                        echo 'Building backend...'
                        sh 'docker build -t my-backend:latest -f backend/Dockerfile .'
                    }
                }
            }
        }
	stage('deploy'){
		steps{
			sh 'docker-compose down && docker-compose up -d '
		}
	}
    }
}
