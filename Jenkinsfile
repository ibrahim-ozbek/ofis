pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('bardak')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t eaglehaslanded/ofis:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push eaglehaslanded/ofis:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}