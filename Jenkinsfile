'''
pipeline {
    agent any  
    stages {
        stage('Hello world') {
            steps {
                sh " echo Hello world "
            }
        }
    }
}
'''
pipeline {
    agent any
    environment {
        ENV_URL="pipeline.google.com"
        AWS_ACCESS_KEY = credentials('AWS_ACCESS_KEY') 
        AWS_SECRET_KEY = credentials('AWS_SECRET_KEY')
        SSH_CRED = credentials('SSH-CRED')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'echo ENV_URL is $ENV_URL'
                sh 'echo AWS_ACCESS_KEY is $AWS_ACCESS_KEY' 
                sh 'echo SSH_CRED is $SSH-CRED'
            }
            
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'echo AWS_SECRET_KEY is $AWS_SECRET_KEY'
            }
        }
        stage('Deploy') {
            environment {
                ENV_URL="stage.google.com"
                sh 'echo AWS_SECRET_KEY is $AWS_SECRET_KEY'
            }
            steps {
                echo 'Deploying....'
                sh 'echo ENV_URL is $ENV_URL'
            }
        }
    }
}