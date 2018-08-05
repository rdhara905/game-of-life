//Declarative//
pipeline{
   agent any
   stages{
      stage('build'){
	steps{
	   echo "Lets build game-of-life"
	   sh 'mvn clean'
	}
      }
      stage('test'){
	steps{
	   echo "Lets.... test the game-of-life"
	}
      }
   }
}
