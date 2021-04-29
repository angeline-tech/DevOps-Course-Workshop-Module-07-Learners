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
                    sh 'pwd'
                }
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
                sh 'pwd'
            }
        }
    }
}