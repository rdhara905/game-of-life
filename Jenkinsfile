//Declarative//
pipeline {
    agent any
    stages {
        stage('Run Project') {
            parallel {
                stage('Build') {
                    steps {
                        echo "Lets build game-of-life"
                        sh 'mvn clean package'
                    }
                }
                stage('Test') {
                    steps {
                        echo "Lets start test cases"
                        sh 'mvn clean'
                        sh 'mvn test'
                        junit '**/target/surefire-reports/*.xml'
                    }
                }
            }
        }
    }
}
