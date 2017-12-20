#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        maven 'mvn3.5.0'
        jdk 'jdk8u141'
    }
    stages {
        stage('run-parallel-actions'){
            parallel{
                stage ('action_a'){
                    steps{
                        echo "Option work in windows"
                    }
                }
                stage ('action_b'){
                    steps{
                        echo "Action B "
                    }
                }
            }
        }
        stage ('Deployment Verification'){
            steps{
                input 'Build all right, deploy to production?'
            }
        }
        stage('Multi-Input') {
            //agent none
            steps {
                script {
                    multi_input = input message: 'Input', ok: 'Release!', parameters: [choice(name: 'MULTI_INPUT',
                            choices: 'Option1\nOption2\nOption3',
                            description: 'Here the description')]
                }
                echo multi_input
            }
        }
    }
    triggers { cron('@daily') }
}
