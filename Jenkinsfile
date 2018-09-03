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
                        sh 'echo $M2_HOME'
                        sh 'export PATH=${M2_HOME}/bin:${PATH}'
                        sh 'echo $MAVEN_OPTS'
                        sh 'echo $JAVA_HOME'
                        sh 'export PATH=${JAVA_HOME}/bin:${PATH}
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
