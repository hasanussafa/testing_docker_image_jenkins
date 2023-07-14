pipeline {
    /*agent { label 'linux'}*/
    agent any
   
    /*options{
        buildDiscarder(logRotator(numToKeepStr: '$'))
         echo "Options worked"
    }*/
    environment {
        echo 'Hello World for testing'
        DOCKERHUB_CREDENTIALS = credentials('jenkins_first_image')
        echo 'environment working'
    }
    stages {
        satge('Build') {
            steps {
                sh 'docker build -t hasanussafa/jenkins_first_image:$BUILD_NUMBER .'
                echo 'Build working'
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
                sh 'docker push hasanussafa/jenkins_first_image:$BUILD_NUMBER'
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
