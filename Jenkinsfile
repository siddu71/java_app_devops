@Library('jenkins_shared_library') _

pipeline{
    agent any 

    stages{
        stage('Git Checkout'){
            steps{
                script{
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/siddu71/java_app_devops.git"
                    )
                }
            }
        }
    }
}