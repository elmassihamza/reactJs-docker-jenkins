pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
                docker build -f Dockerfile-prod -t sample:prod
            }
        }
    }
}