pipeline {
    agent any

    stages {
        stage("Updating docker image tag") {
            steps {
                script {
                GIT_TOKEN = credentials(argocd-deployments-token)
                sh "printenv"
                sh "git config user.email alex.bobkov@icloud.com"
                sh "git config user.name alexbob"
                sh "sed -i 's/alexbob2\\/nebula-poc:[[:digit:]]\\+/alexbob2\\/nebula-poc:${env.BUILD_NUMBER}/' nebula-poc/deployment.yaml"
                sh "git commit -am 'Triggered Build: ${env.BUILD_NUMBER}'"
                sh "git push https://${GIT_TOKEN}@github.com/alexbob/argo-cd-deployment.git main"
                }
            }  
        }
    }
}
