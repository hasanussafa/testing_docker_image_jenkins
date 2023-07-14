pipeline {
    agent { label 'linux'}
    options{
        buildDiscarder(logRotator(numToKeepStr: '$'))
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('jenkins_first_image')
    }
    stages {
        satge('Build') {
            steps {
                sh 'docker build -t hasanussafa/jenkins_first_image:tagname:latest .'
            }
        }
        satge('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        satge('Push') {
            steps {
                sh 'docker push hasanussafa/jenkins_first_image:tagname:latest'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}