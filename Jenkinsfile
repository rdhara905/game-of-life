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
                        label 'slave1'
                    }
                    steps {
                        echo "Lets start test cases"
                        sh 'export M2_HOME=/usr/local/src/apache-maven'
                        sh 'export PATH=${M2_HOME}/bin:${PATH}'
                        sh 'echo $M2_HOME'
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
