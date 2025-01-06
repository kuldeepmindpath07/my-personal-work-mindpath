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
                git url: "https://github.com/knaopel/docker-frontend-backend-db.git", branch: "master"
                echo "clonning successfull"
            }
        }
        stage('build and run'){
            steps{
                sh "docker-compose up -d"
            }
        }
    }
}
