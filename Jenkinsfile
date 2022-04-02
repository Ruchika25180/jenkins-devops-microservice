pipeline {
		agent any
		//agent { docker { image 'maven'} }
		environment{
			dockerHome = tool 'myDocker'
			mavenHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages{
			stage('Checkout'){
				steps{
					echo "PATH $PATH"
					sh 'mvn --version'
					sh 'docker version'
					echo "BUILD_NUMBER $env.BUILD_NUMBER"
					echo "Build2"
				}
			}
			stage('Compile'){
				steps{
					sh "mvn clean compile"
				}
			}
			stage(Test){
				steps{
					sh "mvn test"
				}
			}
			stage('Integration Test'){
				steps{
					sh "mvn failsafe:integration-test failsafe:verify"
				}
			}
			stage('Package'){
				steps{
					sh "mvn package -DskipTests"
				}
			}
			stage('Build Docker Image'){
				steps{
					script{
						dockerImage = docker.build("rucrani/jenkins-devops-microservice:${env.BUILD_TAG}")
					}
				}
			}
			stage('Push Docker Image'){
				steps{
					script{
						//docker.withRegistry('','credentialname'){
							dockerImage.push();
							dockerImage.push('latest');
						//}
					}
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