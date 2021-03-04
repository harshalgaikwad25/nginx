pipeline {



environment {



registry = "harshalgaikwad/nginxtest"



registryCredential = 'DockerHub'



dockerImage = ''



}



agent any



stages {



  stage('Cloning our Git') {



steps {



git 'https://github.com/harshalgaikwad25/nginx.git'



}



}



stage('Building our image') {



steps {



script {



dockerImage = docker.build registry + ":$BUILD_NUMBER"



}



}



}



stage('Deploy our image') {



steps {



script {



docker.withRegistry('https://registry.hub.docker.com/','DockerHub') {



dockerImage.push()



}



}



}



}



stage('Cleaning up') {



steps {



sh "docker rmi $registry:$BUILD_NUMBER"



}



}



}



}
