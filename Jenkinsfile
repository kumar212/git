node ('MAVEN') {

	stage ('SCM') {
		// git clone
		git branch: 'main', url: 'https://github.com/kumar212/spring-petclinic.git'
	}
	
	stage ('build') {
		// build the package
		sh 'mvn package'
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
