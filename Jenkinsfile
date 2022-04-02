pipeline {
		agent { docker { image 'maven:latest'} }
		stages{
			stage('Build2'){
				steps{
					sh 'mvn --version'
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
			unstable {
				echo "run when fail"
			}
			changed {
				echo "run when fail"
			}
		}
}