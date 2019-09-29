pipeline {
  agent any
	tools {
		jdk "JAVA_HOME"
		maven "MAVEN_HOME"
	}
  stages {
	  stage('--Software--'){
		  steps{
			  bat 'java -version'
			  bat 'mvn -version'
			  bat 'echo Testing Completed Successfully !!!!!!..... By SanjaySaravanan'
		  }
	  }
  	stage('--Build--') {
	  steps {
	  bat 'mvn clean package'
	  archiveArtifacts '**/target/*.war'
	  echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
	  }
  	}
	  stage('--Deploy--'){
		  steps {
			  deploy adapters: [tomcat8(credentialsId: 'Tomcat', path: '', url: 'http://localhost:8010')], contextPath: null, war: 'target/altimetrik.war'
		  }
	  }
  }
}
