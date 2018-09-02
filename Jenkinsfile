//Declarative//
pipeline{
   agent any
	parallel {
	   stages{
	      stage('build'){
		steps{
		   echo "Lets build game-of-life"
		   sh 'mvn clean install'
		}
	      }
	     stage('Test'){
	      steps{
		 archiveArtifacts artifacts: "**/target/*.jar"
		 junit '**/target/surefire-reports/*.xml'
	      }
	     }
	  }
	}
}
