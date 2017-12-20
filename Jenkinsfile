#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        maven 'mvn3.5.0'
        jdk 'jdk8u141'
    }
    stages {
        stage('TU') {
            steps {
                sh "mvn clean test"
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('Version') {
            tools {
                maven 'mvn3.3.9'}
            steps {
                sh'mvn -version'
            }
        }
    }
    triggers { cron('@daily') }
}
