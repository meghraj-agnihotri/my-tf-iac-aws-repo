pipeline {
    agent any
    
    tools {
        terraform 'terraform'
    }
    
    environment {
        TF_HOME = tool ('terraform')
        TP_LOG = "WARN"
        PATH = "TF_HOME:$PATH"
        ACCESS_KEY = credentials('AWS_ACCESS_KEY_ID')
        SECRET_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    

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
