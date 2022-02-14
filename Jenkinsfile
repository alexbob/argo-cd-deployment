pipeline {
    agent any

    stages {
        stage("Updating docker image tag") {
            steps {
                sh "git config user.email alex.bobkov@icloud.com"
                sh "git config user.name alexbob"
                sh "sed -i 's/alexbob2\\/nebula-poc:[[:digit:]]\\+/alexbob2\\/nebula-poc:${env.BUILD_NUMBER}/' nebula-poc/deployment.yaml"
                sh "git commit -am 'Triggered Build: ${env.BUILD_NUMBER}'"
                sh "git push origin main"
            }  
        }
    }
}
