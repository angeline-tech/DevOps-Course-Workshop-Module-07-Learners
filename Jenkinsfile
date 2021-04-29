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
                sh 'npm --v'
            }
        }
        stage('Build & Test dotnet') {

            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/sdk:5.0'
                }
            }
            steps {
                sh 'dotnet --list-sdks'
            }
        }
    }
}