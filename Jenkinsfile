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
    agent { label 'javaa' }
    
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
    tools {
        maven 'maven-3.5.0' 
    }
    stages {
        stage('Parallel Stage') {
            parallel {
            stage('First Stage Name') {
                steps {
                    sh "hostname"   // I want this job to run this on WS
                    sh 'mvn --version'
                    sh "echo One"
                    sh "env"
                    sh "sleep 10"
                }
            }
            stage('Second Stage Name') {
                steps {
                    sh "echo One"
                    sh "echo ENV_URL is ${ENV_URL}"
                    sh "echo $AWS_ACCESS_KEY"
                    sh "sleep 20"
                }
            }
            stage('Third Stage Name') {
                environment {
                    ENV_URL = "stage.google.com"
                }
                steps {
                    sh "echo ENV_URL is ${ENV_URL}"
                    sh "sleep 21"
                    }
                }
            }    
        }
    }
}