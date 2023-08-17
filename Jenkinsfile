pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from GitHub
                git 'https://github.com/manasvi19/web-application.git'
            }
        }

        stage('Restore Packages') {
            steps {
                // Restore NuGet packages
                sh 'dotnet restore'
            }
        }

        stage('Build with MSBuild') {
            steps {
                // Use MSBuild to build the solution
                withMSBuild(
                    msBuildName: 'MSBuild', // Name of your MSBuild installation in Jenkins
                    msBuildFile: 'Webapplication1.sln',
                    targets: 'Build',
                    properties: [
                        'Configuration=Release'
                    ]
                )
            }
        }
    }
}
