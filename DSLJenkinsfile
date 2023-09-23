pipeline {
    agent any
    stages {
        stage('code compile') {
            steps {
               //sh 'npm install'
               print 'OK'
            }
        }
        stage('test cases') {
            steps {
               //sh 'npm test'
               print 'OK'
            }
        }
        stage('code quality') {
            //parameters {
            //    password(name: 'SONAR.PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
            //}
            steps {
               //sh 'sonar command'
               print 'OK'
            }
        }
        stage('code security') {
            when {
                expression { env.BRANCH_NAME == "main" }
            }
            steps {
               //sh 'checks with SAST & SCA'
               print 'OK'
            }
        }
        stage('Release') {
            when {
                expression { env.TAG_NAME ==~ ".*"}
            }
            //parameters {
            //    password(name: 'NEXUS.PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
            //}
            steps {
               //sh 'Upload artifact to nexus repo'
               print 'OK'
            }
        }
    }
}