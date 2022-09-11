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
        
    }
}
