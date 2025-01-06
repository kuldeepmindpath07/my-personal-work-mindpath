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
		sh "docker images"
            }
        }
	stage ('push to dockerhub'){
	    steps{
	    	sh "docker login  -u kuldeep433 -p Lala@2003ji"
		sh "docker image tag three-tier_web:latest kuldeep433/three-tier_web"
		sh "docker image tag three-tier_api:latest kuldeep433/three-tier_api"    
		sh "docker push kuldeep433/three-tier_api"
		sh "docker push kuldeep433/three-tier_api"
	    }
	}
    }
}
