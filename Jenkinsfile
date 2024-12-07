pipeline {
    agent any

    environment {
        SALEOR_HOSTNAME = 'your-saleor-hostname' // Set this environment variable or replace it directly
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install npm globally
                    sh 'npm i -g @saleor/cli@latest'
                    // Install npm via apt if not already installed
                    sh 'sudo apt update && sudo apt install -y npm'
                    // Install pnpm via apt if not already installed
                    sh 'sudo apt install -y pnpm'
                }
            }
        }

        stage('Clone Saleor Storefront') {
            steps {
                script {
                    // Clone Saleor storefront repository
                    sh 'git clone https://github.com/saleor/storefront.git'
                    // If necessary, use sudo for the git clone (though typically not needed)
                    // sh 'sudo git clone https://github.com/saleor/storefront.git'
                }
            }
        }

        stage('Set Up Environment') {
            steps {
                script {
                    // Copy the example .env file to .env
                    sh 'cp .env.example .env'
                    // Optionally, use sudo (not recommended unless required)
                    // sh 'sudo cp .env.example .env'
                }
            }
        }

        stage('Install Dependencies using pnpm') {
            steps {
                script {
                    // Install dependencies using pnpm
                    sh 'pnpm install'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed!'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
