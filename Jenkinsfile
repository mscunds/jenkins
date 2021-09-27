CODE_CHANGES = getGitChanges()

pipeline {
    agent any
    stages{
        stage("codereview") {
            steps {
                echo 'call sonar for codecheck'
            }
        }
        stage("build") {
            when {
                expression {
                    (CODE_CHANGES == true)
                }
            }
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
            echo "success"
        }
        failure {
            echo 'failed'
        }
    }
}
