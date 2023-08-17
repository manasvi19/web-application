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
                    sh 'dotnet restore'
                    sh 'dotnet build Webapplication1.csproj --configuration Release'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    // Publish your app
                    sh 'dotnet publish Webapplication1.csproj --configuration Release --output ./publish'
                }
            }
        }

        stage('Display URL') {
            steps {
                script {
                    def serverUrl = 'http://localhost:5146' // Adjust the port as needed
                    echo "Published website URL: ${serverUrl}"
                }
            }
        }
    }
}
