pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('SampleCredential')
    }
    tools {
        maven 'Maven'
    }
    parameters {
        choice(name: 'Version', choices: ['1.1.0', '1.2.0', '1.3.0'])
        booleanParam(name: 'deploy', defaultValue: false)
    }
    stages{
        stage("codereview") {
            steps {
                echo 'call sonar for codecheck'
            }
        }
        stage("build") {
            steps {
                echo 'build the application'
                sh "mvn --version"
                sh "java -version"
            }
        }
        stage("component-test") {
            steps {
                echo 'execute componen tests'
            }
        }
        stage("integration-test") {
            steps {
                echo 'execute integration tests'
                withCredentials([usernamePassword(credentialsId: 'SampleCredential', usernameVariable: 'USER', passwordVariable: 'PWD')]) {
                    echo "execute some shell with ${USER} and ${PWD}"
                }
            }
        }
        stage("deploy") {
            when {
                expression {
                    BRANCH_NAME == 'dev' || params.deploy
                }
            }
            steps {
                echo 'deploy the application'
                echo "deploying using credentials ${SERVER_CREDENTIALS}"
                echo "deploying version ${Version}"
            }
        }
    }
    post {
        always {
            echo 'do it always'
        }
        success {
            echo "${NEW_VERSION} successfully processed"
        }
        failure {
            echo "${NEW_VERSION} failed"
        }
    }
}
