pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                bat 'mvn install'
            }
        }
	  stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.5') {
                        bat 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}
