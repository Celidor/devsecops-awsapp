#!groovy

pipeline {
    agent any

    environment {
        AWS_REGION = 'eu-west-1'
    }

    stages {
        stage('Build'){
            steps {
                sh 'npm i'
            }
        }
        stage('Unit Test'){
            steps {
                sh 'npm test'
            }
        }
        stage('Dev (Deploy)') {
            environment {
                AWS_STAGE = 'dev'
            }
            steps {
              withCredentials([[
                $class: 'AmazonWebServicesCredentialsBinding',
                credentialsId: 'aws-key',
                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
              ]]) {
                sh 'serverless deploy -s dev'
                }
            }
        }
        stage('Test (Deploy)') {
            environment {
                AWS_STAGE = 'test'
            }
            steps {
              withCredentials([[
                $class: 'AmazonWebServicesCredentialsBinding',
                credentialsId: 'aws-key',
                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
              ]]) {
                sh 'serverless deploy -s test'
                }
            }
        }
        stage('Prod (Deploy)'){
            environment {
                AWS_STAGE = 'prod'
            }
            steps {
              withCredentials([[
                $class: 'AmazonWebServicesCredentialsBinding',
                credentialsId: 'aws-key',
                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
              ]]) {
                sh 'echo deploying to prod'
                sh 'serverless deploy -s prod'
                }
            }
        }
    }
}
