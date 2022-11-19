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
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo 'ENV_URL is $(ENV_URL)'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}