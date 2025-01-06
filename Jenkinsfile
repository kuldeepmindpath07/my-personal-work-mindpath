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
    }
}
