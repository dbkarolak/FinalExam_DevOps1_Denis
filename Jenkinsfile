pipeline{
    agent {
        docker {
            image 'node:18.17.1-alpine3.18'
        }
    }

    environment {
    FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }

    stages{
        stage('Building'){
            steps{
            sh 'npm install -g firebase-tools'
            }
        } 

         stage('Testing'){
            steps{
            sh 'firebase deploy -P finalexam-testing-denis --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }

        stage('Staging'){
            steps{
            sh 'firebase deploy -P finalexam-staging-denis --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }

        stage('Production'){
            steps{
            sh 'firebase deploy -P finalexam-production-denis --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }
    }
}