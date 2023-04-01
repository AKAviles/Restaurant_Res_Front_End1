#!/usr/bin/env groovy 


pipeline {
    agent any

    environment {
        AWS_ECR_URL = '014920475271.dkr.ecr.us-east-1.amazonaws.com/quote-machine'
        AWS_ECR_NAME = 'restaurant-reservation/web'
        
    }

    stages {
        stage('Build Docker Image - tried version') {
            steps {
                script {
                    docker.build("${AWS_ECR_NAME}")
                }
            }
        }

       stage('Deploy Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://014920475271.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:aws-resources') {
                        docker.image("${AWS_ECR_NAME}").push('latest')
                    }
                }
            }
       }
    }
}