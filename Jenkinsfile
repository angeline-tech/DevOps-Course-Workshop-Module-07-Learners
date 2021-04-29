pipeline {
    agent none
    stages {
        stage('Build & Test Node') {
             agent {
                docker {
                    image 'node:14-alpine'
                }
            }

            steps {
                dir("DotnetTemplate.Web"){
                    sh 'npm --v'
                    sh 'npm install'
                    sh 'npm t'
                }
            }
        }
        stage('Build & Test dotnet') {
            environment {
                DOTNET_CLI_HOME = '/tmp/dotnet_cli_home'
            }
            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/sdk:5.0'
                }
            }
            steps {
                sh 'dotnet --list-sdks'
                sh 'dotnet build'
                sh 'dotnet test'
            }
        }
    }
}