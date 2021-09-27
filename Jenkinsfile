pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
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
            }
        }
        stage("deploy") {
            when {
                expression {
                    (BRANCH_NAME == 'dev')
                }
            }
            steps {
                echo 'deploy the application'
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
