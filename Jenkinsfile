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
		sh 'mvn clean verify admin:admin -Dsonar.login=$sqa_df332b7b17b1c500bb4ae5b79c8829c8e1c9956a'
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
    
