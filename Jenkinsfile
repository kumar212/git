node ('MAVEN') {

	stage ('SCM') {
		// git clone
		git branch: 'main', url: 'https://github.com/kumar212/git.git'
	}
	
	stage ('build') {
		// build the package
		sh 'mvn package'
	}

        stage ('SonarQube analysis') {
                // performing sonarqube analysis 
		withSonarQubeEnv('SONAR') {
		sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.8.7:sonar'
	   }
        }

	stage ('test') {
	    // junit test
	    junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
	}
	
	stage ('archival') {
		// archiving artifacts
		archiveArtifacts artifacts: 'target/*.jar'
	}

}	
