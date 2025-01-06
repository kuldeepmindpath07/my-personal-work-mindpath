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
		sh "docker stop db_cont && docker rm db_cont"
		sh "docker stop django_app && docker rm django_app"    
                sh "docker-compose up -d --remove-orphans"
            }
        }
    }
}
