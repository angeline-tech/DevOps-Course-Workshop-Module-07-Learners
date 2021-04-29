pipeline {
    agent none
    stages {
        stage('spin up node agent') {
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
                stage("Install npm dependencies"){
                    steps{
                        dir("DotnetTemplate.Web"){
                            sh 'npm install'
                        }
                    }
                }
                stage("npm test"){
                    steps{
                        dir("DotnetTemplate.Web"){
                            sh 'npm t'
                        }
                    }
                }   
            }

        }
        stage('spinup dotnet agent') {
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
                stage("dotnet build"){
                    steps{
                        sh 'dotnet build'
                    }
                }            
                stage("dotnet test"){
                    steps{
                        sh 'dotnet test'
                    }
                }
            }
        }
    }
}