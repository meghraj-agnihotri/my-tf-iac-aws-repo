pipeline {
    agent any
    
    tools {
        terraform ('terraform')
     
    }
    environment {
        TF_HOME = tool('terraform')
        ACCESS_KEY = credentials('AWS_ACCESS_KEY_ID')
        SECRET_KEY = credentials('AWS_SECRET_ACCESS_KEY')
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
        
        
    }
}
