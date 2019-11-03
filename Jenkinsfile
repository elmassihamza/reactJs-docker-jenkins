pipeline {
    agent any
    stages {
        stage('Example') {
            environment {
                SERVICE_CREDS = credentials('4f8b6b5b-f947-44e2-a179-66da58ca5cfa')
            }
            steps {
                withDockerRegistry([ credentialsId: "f1abf523-1065-4476-8a19-6819799fc176", url: "" ]) {
                    sh 'docker build -f Dockerfile-prod -t phemox/repo:react-prod .'
                    sh 'docker push phemox/repo:react-prod'
                }
                sshagent(credentials : ['4f8b6b5b-f947-44e2-a179-66da58ca5cfa']) {
                    sh 'ssh ec2-user@ec2-35-180-86-208.eu-west-3.compute.amazonaws.com "sudo docker stop phemox && sudo docker container rm phemox && sudo docker pull phemox/repo:react-prod && sudo docker run -d --name phemox -p 80:80 phemox/repo:react-prod"'
                }
            }
        }
    }
}