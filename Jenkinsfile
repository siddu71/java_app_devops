@Library('jenkins_shared_library') _

pipeline{
    agent any 

    parameters{
        choice(name: 'Action', choices: 'create\ndestroy', description: 'Choose Create/Destroy')
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
                    staticCodeAnalysis()   
                }
            }
        }
        
    }
}