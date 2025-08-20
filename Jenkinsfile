pipeline {
    agent {
        label 'AGENT-1'
    }
    environment { 
        appVersion = '1.0'
        REGION = "us-east-1"
        ACC_ID = "315069654700"
        PROJECT = "roboshop"
        COMPONENT = "catalogue"
    }
/*     environment {
        COURSE = 'Jenkins'
    } */
    options {
        timeout(time: 30, unit: 'MINUTES') // Pipeline will abort after 1 hour
        disableConcurrentBuilds()
    }
/*     parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Specify the jenkins user name')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run unit tests?')
    } */
    stages {
        stage('Read package.json') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "Package version: ${appVersion}"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                   sh """
                        npm install
                   """
                }
            }
        }
        stage('Test'){
            steps {
                script {
                    sh """
                        echo "Hello from Test stage.."
                    """
                }
                
            }
        }
        
    }
    post {
        always {
            echo "I will always say Hello.."
            deleteDir()
        }
        success {
            echo "Hello SUCCESS.."
        }
        failure {
            echo "Hello FAILURE..."
        }
    }    
}
