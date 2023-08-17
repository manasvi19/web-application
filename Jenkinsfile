pipeline {
    agent any

    stages {
        // Add the deleteDir() command here to clear the workspace
        stage('Preparation') {
            steps {
                deleteDir() // Clear the workspace before each build
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'dotnet restore'
                sh 'dotnet build --configuration Release'
            }
        }
        
        stage('Publish') {
            steps {
                sh 'dotnet publish --configuration Release --output ./publish'
            }
        }
        
        stage('Run App and Open URL') {
            steps {
                script {
                    // Change this to the correct path to your published app
                    def appPath = '/Users/manasvidhankani/Downloads/WebApplication1/publish'
                    def port = 5000 // Change to your app's port
                    
                    sh "cd ${appPath}"
                    sh "dotnet Webapplication1.dll &"
                    sh 'sleep 10'
                    sh "open http://localhost:${port}"
                }
            }
        }
    }
}
