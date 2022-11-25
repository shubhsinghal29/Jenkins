pipeline{

	agent {label 'Devops'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Devops')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/shubhsinghal29/nodeapp_test.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t shubhsinghal29/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push shubhsinghal29/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
