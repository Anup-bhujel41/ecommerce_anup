pipeline{
agent any
environment {
DOCKERHUB_CREDENTIALS = credentials('anupbhujel-dockerhub')
}
stages{
	stage('Cloning git'){
		steps{
		git 'https://github.com/Anup-bhujel41/ecommerce_anup.git'
		}
	}
	
	stage('Build Docker image') {
		steps {
			sh 'docker build . -t anup/ecom:$BUILD_NUMBER'
		}
	}

	stage('Login into Dockerhub') {
		steps {
			sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
		}
	}
	
	stage('push image') {
		steps {
			sh 'docker push anup/ecom:$BUILD_NUMBER'
		}
	}
}
post {
	always {
		sh 'docker logout'
		}
	}
}
