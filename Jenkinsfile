pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
                script {
                    def dockerfile = 'Dockerfile-prod'
                    def customImage = docker.build("sample:prod", "-f ${dockerfile} .")
                }
            }
        }
    }
}