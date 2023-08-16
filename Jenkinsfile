pipeline {
    agent any

    environment {
        DOTNET_CLI_TELEMETRY_OPTOUT = '1'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout your code from GitHub
                    git 'https://github.com/manasvi19/web-application.git'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build your ASP.NET Core app
                    bat 'dotnet restore'
                    bat 'dotnet build --configuration Release'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    // Publish your app
                    bat 'dotnet publish --configuration Release --output ./publish'
                }
            }
        }

        stage('Display URL') {
            steps {
                script {
                    def serverUrl = 'http://localhost:5146' // Change this to your server URL
                    echo "Published website URL: ${serverUrl}"
                }
            }
        }
    }
}
