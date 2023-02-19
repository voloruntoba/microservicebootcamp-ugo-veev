pipeline {
    agent any

stages {
        stage('Gitclone') {
            steps {
                sh 'git clone https://github.com/voloruntoba/Google-Kubernetes-boilerplate.git'
            }
        }    
        stage('Build & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockercred', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                sh 'cd Google-Kubernetes-boilerplate/app/adservice && docker build -t adservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag adservice   $dockeruser/adservice:latest'
                sh 'docker push $dockeruser/adservice:latest'
                sh 'cd . && cd Google-Kubernetes-boilerplate/app/cartservice/src/ && docker build -t cartservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag cartservice   $dockeruser/cartservice:latest'
                sh 'docker push $dockeruser/cartservice:latest'
                sh 'cd . && cd Google-Kubernetes-boilerplate/app/cartservice/src/ && docker build -t cartservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag cartservice   $dockeruser/cartservice:latest'
                sh 'docker push $dockeruser/cartservice:latest'
                sh 'cd . && cd Google-Kubernetes-boilerplate/app/checkoutservice/ && docker build -t checkoutservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag checkoutservice   $dockeruser/checkoutservice:latest'
                sh 'docker push $dockeruser/checkoutservice:latest'
				//remove all images 
				sh  'docker rmi -f $(docker images -aq) && docker system prune -f'
                //				
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/currencyservice/ && docker build -t currencyservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag currencyservice   $dockeruser/currencyservice:latest'
                sh 'docker push $dockeruser/currencyservice:latest'
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/emailservice/ && docker build -t emailservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag emailservice   $dockeruser/emailservice:latest'
                sh 'docker push $dockeruser/emailservice:latest'
				//remove all images 
				sh  'docker rmi -f $(docker images -aq) && docker system prune -f'
				//
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/frontend/ && docker build -t frontend .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag frontend   $dockeruser/frontend:latest'
                sh 'docker push $dockeruser/frontend:latest'
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/loadgenerator/ && docker build -t loadgenerator .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag loadgenerator   $dockeruser/loadgenerator:latest'
                sh 'docker push $dockeruser/loadgenerator:latest'
				//remove all images 
				sh  'docker rmi -f $(docker images -aq) && docker system prune -f'
				//
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/paymentservice/ && docker build -t paymentservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag paymentservice   $dockeruser/paymentservice:latest'
                sh 'docker push $dockeruser/paymentservice:latest'
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/productcatalogservice/ && docker build -t productcatalogservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag productcatalogservice   $dockeruser/productcatalogservice:latest'
                sh 'docker push $dockeruser/productcatalogservice:latest'
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/recommendationservice/ && docker build -t recommendationservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag recommendationservice   $dockeruser/recommendationservice:latest'
                sh 'docker push $dockeruser/recommendationservice:latest'
				sh 'cd . && cd Google-Kubernetes-boilerplate/app/shippingservice/ && docker build -t shippingservice .'
                sh 'docker login -u $dockeruser -p $dockerpass'
                sh 'docker tag shippingservice   $dockeruser/shippingservice:latest'
                sh 'docker push $dockeruser/shippingservice:latest'
				//remove all images 
				sh  'docker rmi -f $(docker images -aq) && docker system prune -f'
				//remove git hub repo
				sh 'cd ../../../'
				sh 'rm -rf Google-Kubernetes-boilerplate'
            }
        }
     }
        }
    }
