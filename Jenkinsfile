pipeline {
    /*agent { label 'linux'}*/
    agent any
    
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World for testing'
            }
        }
    }

    options{
        buildDiscarder(logRotator(numToKeepStr: '$'))
        echo "Options function worked"
    }
    environment {
        echo 'Hello World'
        DOCKERHUB_CREDENTIALS = credentials('jenkins_first_image')
        echo 'Hello environment'
    }
    stages {
        satge('Build') {
            steps {
                sh 'docker build -t hasanussafa/jenkins_first_image:latest .'
                echo 'Hello Build'
            }
        }
        satge('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                echo 'Hello Login'
            }
        }
       
        satge('Push') {
            steps {
                sh 'docker push hasanussafa/jenkins_first_image:latest'
                echo 'Hello Push'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
            echo 'Hello Logout'
        }
    }
}