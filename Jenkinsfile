#!/usr/bin/env groovy
pipeline {
    agent any
    stages {
        stage('Pull Latest Image') {
            steps {
                bat 'docker pull docker-image-name'
            }
        }
        stage('Start Grid') {
            steps {
                bat 'docker-compose up -d hub chrome firefox'
            }
        }
        stage('Run Test') {
            steps {
                bat 'docker-compose up sample-module-chrome sample-module-firefox'
            }
        }
    } // stages
    post {
        always {
            archiveArtifacts artifacts: 'output/**'
            bat 'docker-compose down'
        }
    } // post
} // pipeline