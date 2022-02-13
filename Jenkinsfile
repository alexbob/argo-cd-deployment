pipeline {
    agent any

    stages {
        stage("Updating docker image tag") {
            sh "sed -i 's/alexbob2\\/nebula-poc:[[:digit:]]\\+/alexbob2\\/nebula-poc:${env.BUILD_NUMBER}/' argo-cd-deployment/nebula-poc/deployment.yaml"
            sh "git commit -am 'Triggered Build: ${env.BUILD_NUMBER}'"
            sh "git push https://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@github.com/alexbob/argo-cd-deployment.git"
             
        }
    }

}
