pipeline {
    agent any
    environment {
        ACCESS_KEY = credentials('private-key')
        SECRET_KEY = credentials('secret-key')
    }
    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ilekicgrid/Terraform-for-jenkins.git']]])

          }
        }

        stage ("terraform init") {
            steps {
                sh ('terraform init -upgrade')
            }
        }

        stage ("terraform Action") {
            steps {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve -var-file="secrets.tfvars"')
           }
        }
    }
}