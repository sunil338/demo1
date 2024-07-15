pipeline {

	agent any
	triggers {
  cron '* * * * * '
}
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
				withCredentials([usernameColonPassword(credentialsId: '39f51006-4e86-4d30-a082-28edff8d27d1', variable: 'login')]) {
    sh 'docker login'
}
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
