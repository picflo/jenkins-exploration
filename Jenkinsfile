#!/usr/bin/env groovy

@Library('emailName') _
//Name of library configure in Jenkins configuration

pipeline {
    agent any
    tools {
        maven 'mvn3.5.0'
        jdk 'jdk8u141'
    }
    stages {
        stage('EmailList') {
            steps {
                mail to: emailList(), subject: "JobDemo", body: "build #${env.BUILD_NUMBER} – Job demo !"
                //emailList is the Name of the file placed inside the folder ./vars in the repository set for 'emailName'
            }
        }
    }
    triggers { cron('@daily') }
}

/*emailList file */
/*
#!/usr/bin/env groovy

def call() {
    Name = "your-email@address.com"
    return Name
}
*/
