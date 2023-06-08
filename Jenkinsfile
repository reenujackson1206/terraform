pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'feature/aws', credentialsId: 'github-userpass', url: 'https://github.com/reenujackson1206/terraform.git'
            }
        }
        stage('terraform format check') {
            steps{
                sh 'cd terraform-aws'
                sh 'terraform fmt'
            }
        }
        stage('terraform Init') {
            steps{
                sh 'pwd'
                sh 'terraform init'
            }
        }
        stage('terraform apply') {
            steps{
                sh 'pwd'
                sh 'terraform apply --auto-approve'
            }
        } 
    }
}


