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
				echo "Deployment Started for staging server"
				build job: "deploy-to-staging-pipeline"
			}

			post{
				success{
					echo "war file successfully deployed on staging server"
				}
			}
		}


		stage('Deploy to production'){
			steps{
				timeout(time:5,unit:'DAYS'){
					input message:"Approve producton deployment ?",submitter:'admin'
				}

				echo "Deployment Started for production server"

				build job: "deploy-to-production-pipeline"
			}

			post{
				success{
					echo "war file successfully deployed on production server"
				}

				failure{
					echo "Deployment failed"
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