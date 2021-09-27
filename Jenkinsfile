pipeline {
    agent any
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
            echo "success"
        }
        failure {
            echo 'failed'
        }
    }
}
