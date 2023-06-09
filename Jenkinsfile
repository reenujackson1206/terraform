pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                sh 'mkdir ~/terraform-code'
                sh 'cd ~/terraform-code'
                git branch: 'feature/aws', credentialsId: 'github-userpass', url: 'https://github.com/reenujackson1206/terraform.git'
            }
        }
        stage('terraform format check') {
            steps{
                sh 'cd ~/terraform-code/terraform/terraform-aws'
                sh 'terraform fmt'
            }
        }
        stage('terraform Init') {
            steps{
                sh 'cd ~/terraform-code/terraform/terraform-aws'
                sh 'terraform init'
            }
        }
        stage('terraform apply') {
            steps{
                sh 'cd ~/terraform-code/terraform/terraform-aws'
                sh 'terraform apply --auto-approve'
            }
        } 
    }
}


