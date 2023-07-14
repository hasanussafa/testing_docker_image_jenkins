pipeline {
    /*agent { label 'linux'}*/
    agent any

    options{
        buildDiscarder(logRotator(numToKeepStr: '$'))
        echo "Options function worked"
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('jenkins_first_image')
        echo "environment function worked"
    }
    stages {
        satge('Build') {
            steps {
                sh 'docker build -t hasanussafa/jenkins_first_image:tagname:latest .'
                echo "Build function worked"
            }
        }
        satge('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                echo "Login worked"
            }
        }
        satge('Push') {
            steps {
                sh 'docker push hasanussafa/jenkins_first_image:tagname:latest'
                echo "Push worked"
            }
        }
    }
    post {
        always {
            sh 'docker logout'
            echo "Logout worked"
        }
    }
}