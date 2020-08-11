pipeline {

    agent {
        docker {
            image 'bryandollery/terraform-packer-aws-alpine'
            args "-u root --entrypoint=''"
        }
    }

       stages {
         stage ('build') {
            steps {
             sh 'packer build packer.json'
            }
        }
        stage ('test') {
            steps {
                sh "docker run --rm manifest-holder"
            }
        }
        stage ('release') {
            environment {
                CREDS = credentials('amerah-creds')
                AWS_ACCESS_KEY_ID = "$CREDS_USR"
                AWS_SECRET_ACCESS_KEY = "$CREDS_PSW"
                OWNER = 'amerah'
                PROJECT_NAME = 'web-server'
           }
  }
 } 
} 
