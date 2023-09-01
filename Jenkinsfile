@Library('jenkins-shared-library')_



pipeline {
    agent any
    tools {
        nodejs "node"
    }
    stages {
        stage('increment version') {
            steps {
                script {
                    
                    incrementVersion()

                   
                }
            }
        }
        stage('Run tests') {
            steps {
               script {

                appTest()

               }
            }
        }
        stage('Build and Push docker image') {
            steps {
               script {

                buildimage()

               }
            }
        }
        stage('commit version update') {
            steps {
                script {
                    versionUpdate()
                }
            }
        }
    }
}

