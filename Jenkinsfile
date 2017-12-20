#!/usr/bin/env groovy

pipeline {
    agent none
    stages {
        stage("first agent") {
            agent any
            steps {
                echo "Can work thanks to any"
            }
        }
        stage("second agent") {
            agent any
            steps {
                echo "Can work thanks to any"
            }
        }
    }
}
