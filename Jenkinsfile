pipeline {
    agent any

    stages {
        stage('Gitclone') {
            steps {
                sh 'git clone https://github.com/voloruntoba/microservicebootcamp-ugo-veev.git'
            }
        }    
        stage('Build & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockercred', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                    sh 'cd microservicebootcamp-ugo-veev/app/frontend && docker build -t frontend .'
                    sh 'docker login -u $dockeruser -p $dockerpass'
                    sh 'docker tag frontend $dockeruser/frontend:latest'
                    sh 'docker push $dockeruser/frontend:latest'
                    // Remove all images 
                    sh 'docker rmi -f $(docker images -aq) && docker system prune -f'
                    // Remove git hub repo
                    sh 'cd ../../../'
                    sh 'rm -rf microservicebootcamp-ugo-veev'
                }
            }
        }
        stage("connect to deploy server") {
            environment { 
                SSH_CRED = credentials('bootcampeks')
            }
            steps {
                script {
                    sh """
                    #!/bin/bash
                    ssh -i "$SSH_CRED" -o StrictHostKeyChecking=no ubuntu@ec2-35-182-97-125.ca-central-1.compute.amazonaws.com << EOF
                    git clone https://github.com/voloruntoba/microservicebootcamp-ugo-veev.git
                    cd microservicebootcamp-ugo-veev
                    git checkout frontend
                    kubectl apply -f kubernetes-bootcamp
                    exit
                    EOF
                    """
                }
            }
        }			
    }
}

