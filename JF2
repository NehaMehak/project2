pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('nehamehak/jenkinsdocker')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t nehamehak/jenkinsdocker:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push nehamehak/jenkinsdocker:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
