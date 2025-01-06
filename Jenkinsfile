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
	stage ('push to dockerhub'){
	    steps{
	    	sh "docker login  -u kuldeep433 -p Lala@2003ji"
		sh "docker kuldeep433/push docker-frontend-backend-db_api_1"
		sh "docker kuldeep433/push docker-frontend-backend-dp_web_1"
		sh "docker kuldeep433/push docker-frontend-backend-db-mango_1"
	    }
	}
        stage('build and run'){
            steps{
		echo "done done done"  
		sh "docker stop nginx_cont && docker rm nginx_cont"
                sh "docker-compose up -d --remove-orphans"
            }
        }
    }
}
