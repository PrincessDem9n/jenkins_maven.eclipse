pipeline {
	agent any
	tools{
		maven 'maven 3.9.9'
		jdk 'Java JDK 17'
		sonar 'sonarqube_scanner'
	}
	// Declare stages clean, test and install
	//splitting it in different stages so that
	//based on the different plugins, we can view the test results based onstages
	// -DskipTests is to prevent the test from running multiple times. 
	//“bat” (batch file) for windows machine
	//for Linux machine Please configure it to “sh” instead of bat
	stages{
		stage("clean"){
			steps{
				echo "Start Clean"
				bat "mvn clean"
			}
		}
		stage("test"){
			steps{
				echo "Start Test"
				bat "mvn test"
			}
		}
		stage("build"){
			steps{
				echo "Start build"
				bat "mvn install -DskipTests"
			}
		}
		stage("sonar"){
			steps{
				echo "Start Sonarqube"
				bat "sonarqube"
				
			}
		}
	}

}