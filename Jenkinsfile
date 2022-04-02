pipeline {
		agent any
		stages{
			stage('Build2'){
				steps{
					echo "Build2"
				}
			}
			stage('Test1'){
				steps{
					echo "Test2"
				}
			}
			stage(IntegrationTest1){
				steps{
					echo "IntegrationTest2"
				}
			}
		} 
		post {
			always {
				echo "always run"
			}
			success {
				echo "run when success1"
			}
			failure {
				echo "run when fail"
			}
		}
}