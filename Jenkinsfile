pipeline {
    /*agent { label 'linux'}*/
    agent any
   
    options{
        buildDiscarder(logRotator(numToKeepStr: '$'))
         
    }
    environment {
        
        DOCKERHUB_CREDENTIALS = credentials('jenkins_first_image')
       
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t hasanussafa/jenkins_first_image:$BUILD_NUMBER .'
                
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
              
            }
        }
       
        stage('Push') {
            steps {
                sh 'docker push hasanussafa/jenkins_first_image:$BUILD_NUMBER'
                
            }
        }
    }
    post {
        always {
            sh 'docker logout'
            
        }
    }
}
