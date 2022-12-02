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
        stage('Stop Grid') {
            steps {
                bat 'docker-compose down'
            }
        }
    } // stages
} // pipeline