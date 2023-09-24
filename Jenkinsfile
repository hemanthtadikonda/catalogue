pipeline {
    agent any
    parameters {
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    }

    stages {
        stage('code compile') {
            steps {
                //sh 'env'
                //sh 'npm install'
                echo "Password: ${params.PASSWORD}"
                echo "Hello ${params.PERSON}"
                print 'OK'
            }
        }

        stage('Test cases') {
            when  {
                allOf {
                    expression { env.BRANCH_NAME != null }
                    expression { env.TAG_NAME == null }
                }
            }
            steps {
                //sh 'npm test'
                print 'OK'
            }
        }

        stage ('code quality') {
            when {
                allOf {
                    expression { env.BRANCH_NAME != null }
                    expression { env.TAG_NAME == null }
                }
            }

            steps {
                //sh 'sonar-scanner -Dsonar.host.url=http://172.31.92.107:9000 -Dsonar.login=admin -Dsonar.password=${params.SONAR-PASSWORD} -Dsonar.projectKey=catalogue'
                print 'OK'
            }
        }

        stage ('code security') {
            when {
                allOf {
                    expression { env.BRANCH_NAME == "main"}
                    expression { env.TAG_NAME    == null}
                }
            }
            //parameters {
            //    password(name: 'SONAR.PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
            //}
            steps {
                //sh 'checkmarx sast sca'
                print 'OK'
            }
        }

        stage ('Release App') {
            when {
                expression {env.TAG_NAME ==~ ".*"}
            }
            //parameters {
            //    password(name: 'NEXUS.PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
            //}
            steps {
                // sh 'upload artifact to nexus command
                print 'Ok-Ok'
            }

        }
    }

}