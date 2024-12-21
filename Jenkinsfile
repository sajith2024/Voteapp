pipeline {
	agent {
		label 'worker'
	}
	stages {
		stage("Build and Push") {
			steps {
				sh "cd vote"
			}
		}
		stage("Deploy") {
			steps {
				sh "echo kubectl"
			}
		}
	}
}


pipeline {
	agent {
		label 'worker'
	}
	stages {
		stage("Build and Push") {
			steps {
				sh ''
				'
				cd vote
				aws ecr get - login - password--region us - east - 1 | docker login--username AWS--password - stdin 825765415332. dkr.ecr.us - east - 1. amazonaws.com
				docker build - t 825765415332. dkr.ecr.us - east - 1. amazonaws.com / vote: vote - v$ {
					BUILD_NUMBER
				}.
				docker push 825765415332. dkr.ecr.us - east - 1. amazonaws.com / vote: vote - v$ {
					BUILD_NUMBER
				}
				''
				'
			}
		}
		stage("Deploy") {
			steps {
				sh ''
				'
				kubectl set image deployment vote vote = 825765415332. dkr.ecr.us - east - 1. amazonaws.com / vote: vote - v$ {
					BUILD_NUMBER
				}
				kubectl rollout restart deployment vote
					''
				'
			}
		}
	}
}
