
pipeline{

	agent any

	stages{
		stage('Clone the repo'){
			steps{
				git branch:'main', url: 'https://github.com/sid-dev-hub/simple-game-nodejs.git'
			}		
		}

		
		stage('Remove Previous Image') {
		    	steps {
        			script {
            				def imageId = sh(
                				script: "docker images simple-game -q",
                				returnStdout: true
            				).trim()
            			if (imageId) {
                			echo "Removing previous image: ${imageId}"
                			sh "docker rmi -f ${imageId}"
            			} 
				else {
                			echo "No previous image found."
            				}
        			}
    			}
		}

		stage('Building the Docker image'){
			steps{
				script{
					sh "docker build -t simple-game ."
				}
			}
		}
		
		stage('Clean Previous Containers') {
			steps {
        			script {
            				def containerId = sh(
                				script: "docker ps --filter 'publish=3000' -q",
                				returnStdout: true
            				).trim()

            				if (containerId) {
                				echo "Port 3000 is in use by container ${containerId}. Removing it."
                				sh "docker rm -f ${containerId}"
            				} 
					else {
                				echo "Port 3000 is free."
            				}
				
        			}
    			}			
		}

		stage('Running the container'){
                        steps{
                                script{
                                        sh "docker run -d -p 3000:3000 simple-game" 
                                }
                        }
                }

		stage('Completed'){
			steps{
				echo "The game is running at port 3000"
			}
		}
	}
}

