@Library('jenkins_shared_library') _

pipeline{
    agent any 

    parameters{
         choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }

    stages{

        
        stage('Git Checkout'){
            when{ expression{ params.action == 'create' }}
            steps{
                script{
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/siddu71/java_app_devops.git"
                    )
                }
            }
        }
        stage('Unit Test Maven'){
            when{ expression{ params.action == 'create' }}
            steps{
                script{
                    mvnTest()   
                }
            }
        }
        stage('Integration test Maven'){
            when{ expression{ params.action == 'create' }}
            steps{
                script{
                    mvnIntegrationTest()   
                }
            }
        }
        stage('Qualitygate Static Analysis'){
            when{ expression{ params.action == 'create' }}
            steps{
                script{
                    def SonarQubecredentialsId = 'sonarqube-api'
                    staticCodeAnalysis(SonarQubecredentialsId)   
                }
            }
        }
        stage('Qualitygate status check'){
            when{ expression{ params.action == 'create' }}
            steps{
                script{
                    def SonarQubecredentialsId = 'sonarqube-api'
                    QualityGateStatus(SonarQubecredentialsId)   
                }
            }
        }
        stage('Maven Build'){
            when{ expression{ params.action == 'create' }}
            steps{
                script{
                    mvnBuild()  
                }
            }
        }

        
        
    }
}