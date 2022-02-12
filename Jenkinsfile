pipeline{
	agent any
		stages{
			stage('One'){
				steps{
					echo 'Hi, this is a demo'
				}
			}
			stage('Two'){
				steps{
					input('Do you want to preceed')
				}
			}
			stage('Three'){
				when{
					not{
						branch "master"
					}
				}
				steps{
					echo "Hello"
				}
			}
			stage('Four'){
				parallel{
					
					stage('Unit Test'){
						steps{
							echo "Running the unit test..."
						}
					}
					
					stage('Integration Test'){
						agent{
							docker{
								reuseNode true
								image 'ubuntu'
							}
						}
						steps{
							echo "Running the interpretation test..."
						}
					}
				}
			}
		}
}
