pipeline {

	agent any

	
	tools {
  maven 'm360'
}
	
	parameters {
  string defaultValue: 'adi', name: 'name', trim: true
}
	stages {
	  stage('build') {
		steps {
		  sh 'mvn install -DskipTests'
		}
	  }

	  stage('test') {
		  steps {
				sh 'echo new'
			}
		 post {
			 always{
				archiveArtifacts artifacts: 'target/**.jar', followSymlinks: false
				junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
			 }
			}
	  }
		
}

}
