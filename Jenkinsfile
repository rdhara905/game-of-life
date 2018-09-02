//Declarative//
pipeline {
    agent any
    stages {
        stage('Run Project') {
            parallel {
                stage('Build') {
                    steps {
                        echo "Lets build game-of-life"
                        sh 'mvn clean install'
                    }
                }
                stage('Test') {
                    steps {
                        archiveArtifacts artifacts: "**/target/*.jar"
                        sh 'mvn clean test'
                        junit '**/target/surefire-reports/*.xml'
                    }
                }
            }
        }
    }
}
