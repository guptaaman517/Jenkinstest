#!/usr/bin/env groovy
@Library('knx-lib') _

pipeline {
    agent any
    environment {
        ansible_deploy_path  = "${env.workspace}/jenkinstest"
    }

    stages {

       stage('Deploy') {
            steps {
              dir ("${ansible_deploy_path}"){
                       sh("ansible-playbook -i ec2.py file.yaml")
                    }
            }

        }
    }
    post {
       failure {
          notifyBuild('FAILURE', 'at', 'sysalerts@knorex.com')
       }
    }
}