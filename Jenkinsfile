#!/usr/bin/env groovy
pipeline {
    agent any
    stages {
        stage('Start Grid') {
            steps {
                bat 'docker-compose up -d hub chrome firefox'
            }
        }
        stage('Run Test') {
            steps {
                bat 'docker-compose up search-module-chrome search-module-firefox book-flight-module-chrome book-flight-module-firefox'
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