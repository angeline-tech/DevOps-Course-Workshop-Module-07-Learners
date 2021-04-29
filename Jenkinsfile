pipeline {
    agent none
    stages {
        stage('Build & Test Node') {
             agent {
                docker {
                    image 'node:14-alpine'
                }
            }
            stages{
                stage("Check npm is installed"){
                    steps{
                        dir("DotnetTemplate.Web"){
                            sh 'npm --v'
                        }
                    }
                }
                stage("Install Dependencies"){
                    steps{
                        dir("DotnetTemplate.Web"){
                            sh 'npm install'
                        }
                    }
                }
                stage("Test"){
                    steps{
                        dir("DotnetTemplate.Web"){
                            sh 'npm t'
                        }
                    }
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
            stages{
                stage("Check dotnet is installed"){
                    steps{
                        sh 'dotnet --list-sdks'
                    }
                }            
                stage("Build"){
                    steps{
                        sh 'dotnet build'
                    }
                }            
                stage("Test"){
                    steps{
                        sh 'dotnet test'
                    }
                }
            }
        }
    }
}