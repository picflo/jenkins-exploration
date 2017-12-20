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
        stage('Tests TI') {
            steps {
                sh "mvn -Dmaven.test.failure.ignore=true install"
                junit 'target/surefire-reports/**/*.xml'
            }
            post {
                success {
                    mail to: 'florian.picard@berger-levrault.com', subject: 'Stage Success', body: 'TI SUCCESS'
                }
            }
        }
    post {
        success {
            mail to: 'florian.picard@berger-levrault.com', subject: 'Job Success', body: 'Test SUCCESS'
        }
        failure {
            mail to: 'florian.picard@berger-levrault.com', subject: 'Job Failure', body: 'Test FAIL'
        }
        //always, changed, unstable, aborted
    }
    triggers { cron('@daily') }
}

