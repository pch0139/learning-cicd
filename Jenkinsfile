pipeline {
    agent any
    
    parameters {
        booleanParm(name : 'BUILD_DOCKER_IMAGE', defaultValue : true, description : 'BUILD_DOCKER_IMAGE')
        booleanParm(name : 'RUN_TEST', defaultValue : true, description : 'RUN_TEST')
        booleanParm(name : 'PUSH_DOCKER_IMAGE', defaultValue : true, description : 'PUSH_DOCKER_IMAGE')
    }

    environment {
        REGION = "ap-northeast-2"
    }
    stages {
        stage('==== Build Docker Image ====') {
            when {
                expression {
                    return params.BUILD_DOCKER_IMAGE
                }
            }
            steps {
                echo 'Building....'
            }
            post {
                always {
                    echo "post stage"
                }
            }
        }
        stage('==== Test ====') {
            when {
                expression {
                    return params.RUN_TEST
                }
            }
            steps {
                echo 'Testing....'
            }
        }
        stage('==== Deploy ====') {
            when {
                expression {
                    return params.PUSH_DOCKER_IMAGE
                }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}
