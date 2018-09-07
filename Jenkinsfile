//Declarative//
pipeline {
    agent none
    stages {
        stage('Run Project') {
            parallel {
                stage('Build') {
                    agent any
                    steps {
                        echo "Lets build game-of-life"
                        sh 'mvn clean package'
                    }
                }
                
                stage('Test') {
                    agent {
                        labels 'slave1'
                    }
                    steps {
                        echo "Lets start test cases"
                        sh 'echo $PATH'
                        sh 'mvn --version'
                        sh 'mvn clean package'
                        archiveArtifacts artifacts: "**/target/*.jar"
                        junit '**/target/surefire-reports/*.xml'
                    }
                }
            }
        }
    }
}
