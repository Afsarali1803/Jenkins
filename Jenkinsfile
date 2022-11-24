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
    
    //*parameters {
    //*   string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    //*
    //*    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')    
    //*
    //*    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    //*
    //*    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')                  
    //*
    //*    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    //*}
    triggers { cron('H/1 * * * *') }
    options {
        buildDiscarder(logRotator(numToKeepStr: '3')) 
        disableConcurrentBuilds()
        timeout(time: 1, unit: 'MINUTES') 
    }
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
                sh mvn --version
                sh 'echo AWS_SECRET_KEY is $AWS_SECRET_KEY'
            }
        }
        stage('Deploy') {
            environment {
                ENV_URL="stage.google.com"
            }
            steps {
                echo 'Deploying....'
                sh 'echo ENV_URL is $ENV_URL'
                sh 'echo AWS_SECRET_KEY is $AWS_SECRET_KEY'
            }
        }
    }
}