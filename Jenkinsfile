pipeline {
	agent any
	stages {
		stage('SonarQube analysis') {
			steps {
				echo "mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar -Dsonar.host.url=\"${SONAR_HOST_URL}\" -Dsonar.login=\"${SONAR_LOGIN}\""
			}
		}
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
					echo "junit 'target/surefire-reports/*.xml'"
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