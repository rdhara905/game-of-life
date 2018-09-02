//Declarative//
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                parallel {
                echo "Lets build game-of-life"
                sh 'mvn clean install'
                }
            }
        }
            
        stage('Test') {
            steps {
                parallel {
                archiveArtifacts artifacts: "**/target/*.jar"
                junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
