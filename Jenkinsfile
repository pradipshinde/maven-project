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
				bat "mvn clean package"	
			}

			post{
				success{ 
					echo "Now Archiving.."
					archiveArtifacts artifacts: "**/target/*.war"
				}
			}
		}

		stage('Deploy to staging'){
			steps{
				echo "Deployment Started"
				Build job: "deploy-to-staging-pipeline"
			}

			post{
				success{
					echo "war file successfully deployed on staging server"
				}
			}
		}

        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }

	}

}