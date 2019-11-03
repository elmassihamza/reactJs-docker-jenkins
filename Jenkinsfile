pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                withDockerRegistry([ credentialsId: "14d0924a-5ae0-4e89-9eff-65280d569d34", url: "" ]) {
                    sh 'docker build -f Dockerfile-prod -t phemox/repo:react-prod .'
                    sh 'docker push phemox/repo:react-prod'
                }
                sshagent(credentials : ['front-end-ssh']) {
                    sh 'ssh ec2-user@ec2-35-180-86-208.eu-west-3.compute.amazonaws.com "sudo docker stop phemox && sudo docker container rm phemox && sudo docker pull phemox/repo:react-prod && sudo docker run -d --name phemox -p 80:80 phemox/repo:react-prod"'
                }
            }
        }
    }
}
