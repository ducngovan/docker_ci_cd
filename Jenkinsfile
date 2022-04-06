pipeline {
	agent any
	stages {
		stage('Clone git') {
			steps{
				git branch: 'main', url: 'https://github.com/ducngovan/docker_ci_cd.git'
			}
		}
		stage('Docker build and push') {
			steps{
			echo 'Success ...............................'
				withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
				sh 'docker build -t duc1996/demo_jenkins_docker:v1 .'
				sh 'docker push duc1996/demo_jenkins_docker:v1'
				}
			}
		}
		stage('Run container in docker') {
			steps{
				echo 'Docker ...............................'
				sh 'docker run --name demo_jenkins_docker -p 8085:8085 -h demo duc1996/demo_jenkins_docker:v1'
			}
		}
		
	
	}
}