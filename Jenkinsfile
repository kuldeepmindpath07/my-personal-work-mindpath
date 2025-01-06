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
		sh "docker stop a96b5bf7ca7d2fdab36e6d6b980c82eb4803b9c891218e8002c948dd21f60dde"
                sh "docker-compose up -d --remove-orphans"
            }
        }
    }
}
