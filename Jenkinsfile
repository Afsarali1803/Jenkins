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
        AWS_ACCESS_KEY = credentials('my-predefined-secret-text') 
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'echo ENV_URL is $AWS_ACCESS_KEY'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            environment {
                ENV_URL="stage.google.com"
            }
            steps {
                echo 'Deploying....'
                sh 'echo ENV_URL is $ENV_URL'
            }
        }
    }
}