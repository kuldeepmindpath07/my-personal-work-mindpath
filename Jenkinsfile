@Library('share') _
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
		    tryClone("https://github.com/kuldeepmindpath07/jenkins-demo.git","kuldeep")
		}
                echo "clonning successfull"
            }
        }
	
        stage('build and run'){
            steps{
		echo "done done done"  
		sh "docker stop nginx_cont && docker rm nginx_cont"
                sh "docker-compose up -d --remove-orphans"
            }
        }
	stage ('push to dockerhub'){
	    steps{
	    	sh "docker login  -u kuldeep433 -p Lala@2003ji"
		sh "docker image tag docker-frontend-backend-db-api_1:latest kuldeep433/docker-frontend-backend-db-api_1"
		sh "docker image tag docker-frontend-backend-db-mongo_1:latest kuldeep433/docker-frontend-backend-db-mongo_1"
		sh "docker image tag docker-frontend-backend-db-web_1:latest kuldeep433/docker-frontend-backend-db-web_1"    
		sh "docker push kuldeep433/docker-frontend-backend-db_api_1"
		sh "docker push kuldeep433/docker-frontend-backend-dp_web_1"
		sh "docker push kuldeep433/docker-frontend-backend-db-mango_1"
	    }
	}
    }
}
