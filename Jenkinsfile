pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main', url: 'https://github.com/akhilbabu459/storefront.git'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker image build -t akhil1919/saleor-front:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker image push akhil1919/saleor-front:DEV'
            }
        }
    }
}
