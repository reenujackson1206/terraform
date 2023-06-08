pipeline {
    agent any
    stages {
        stage('Install Terraform') {
            steps {
                sh 'wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg'
                sh 'echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list'
                sh 'sudo apt update && sudo apt install terraform'
            }
        }
        stage('Clone') {
            steps {
                git credentialsId: 'github-userpass', url: 'https://github.com/reenujackson1206/terraform.git'
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
                sh 'terraform init'
            }
        }
        stage('terraform apply') {
            steps{
                sh 'terraform apply --auto-approve'
            }
        } 
    }
}


