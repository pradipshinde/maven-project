pipeline{

	agent any

	stages{

		stage('Test'){
			steps{
				echo "Testing..."
			}
		}

		stage('Build'){
			steps{
				echo "Building..."
			}
		}

		stage('Deploy'){
			steps{
				echo "Deployed..."
			}
		}

        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }

	}

}