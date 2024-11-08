pipeline {
    agent any
    
    environment {
        FIREBASE_TOKEN = credentials('firebase_token')  // Define your Firebase token in Jenkins credentials
    }

    stages {
        stage('Building') {
            steps {
                script {
                    // Install Firebase tools if needed
                    sh 'npm install -g firebase-tools'
                }
            }
        }
        
        stage('Testing') {
            steps {
                script {
                    // Deploy to Firebase Testing environment using Webhook
                    sh 'firebase use --add FinalExam_Testing_DAHLIA'
                    sh 'firebase deploy --only hosting --token $FIREBASE_TOKEN'
                }
            }
        }
        
        stage('Staging') {
            steps {
                script {
                    // Deploy to Firebase Staging environment using Webhook
                    sh 'firebase use --add FinalExam_Staging_DAHLIA'
                    sh 'firebase deploy --only hosting --token $FIREBASE_TOKEN'
                }
            }
        }
        
        stage('Production') {
            steps {
                script {
                    // Deploy to Firebase Production environment using Webhook
                    sh 'firebase use --add FinalExam_Production_DAHLIA'
                    sh 'firebase deploy --only hosting --token $FIREBASE_TOKEN'
                }
            }
        }
    }
}
