pipeline {
    agent any

    environment {
        GIT_TOKEN = credentials('argocd-deployments-token')
    }
    

    stages {
        stage("Updating docker image tag") {
            steps {
                echo "In step"
                script { 
                    buildNumber = Jenkins.instance.getItem('nebula-poc-pipeline').getItem('main').lastSuccessfulBuild.number
                }
                echo "${buildNumber}"  
                sh "git config user.email alex.bobkov@icloud.com"
                sh "git config user.name alexbob"
                sh "sed -i 's/alexbob2\\/nebula-poc:[[:digit:]]\\+/alexbob2\\/nebula-poc:${buildNumber}/' nebula-poc/deployment.yaml"
                sh "git commit -am 'Triggered Build: ${buildNumber}'"
                sh "git remote set-url origin https://$GIT_TOKEN@github.com/alexbob/argo-cd-deployment.git"
                sh "git push --set-upstream origin main"                           
            }
        }
    }
}
