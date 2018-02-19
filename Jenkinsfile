pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo 'mvn -B -DskipTests clean package'
			}
		}
		stage('Test') {
			steps {
				echo 'mvn test'
			}
			post {
				always {
					junit 'target/surefire-reports/*.xml'
				}
			}
		}
		stage('Archive') {
			steps {
				archiveArtifacts(artifacts: 'target/')
			}
		}
	}
}