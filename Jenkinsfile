pipeline {
    agent any
    
    tools {
        terraform 'terraform'
    }

    stages {
        stage ('checkout from GitHub') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/meghraj-agnihotri/my-tf-iac-aws-repo.git']]])
            }
        }
        
        stage ("terraform init") {
            steps {
                sh 'terraform init'
            }
        }
        
        stage ("terraform format") {
            steps {
                sh 'terraform fmt'
            }
        }
        
        stage ("terraform Action") {
            steps {
                echo 'terraform action from the parameter is --> ${action}'
                sh 'terraform ${action} --auto-approve'
            }
        }    
    }
}
