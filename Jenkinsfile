pipeline {
    agent any
    tools {
  maven 'maven-3.9.3'
  }
    environment {
      DOCKER_TAG = getVersion()
    }

    stages {

        stage('CLEAN WORKSPACE') {
            steps {
                cleanWs()
            }
        }
         stage('CODE CHECKOUT') {
            steps {
                git 'https://github.com/Praveeen1996/dockeransiblejenkins.git'
            }
        }
        stage('MAVEN BUILD'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('CODE QUALITY REPORT'){
            steps{
                sh "mvn clean sonar:sonar"
            }
        }
        stage('DOCKER BUILD IMAGE'){
            steps{
                sh "docker build . -t praveenhema/hemasreeapp:${DOCKER_TAG} "
            }
        }
        stage('DOCKERHUB PUSH'){
            steps{
                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
                    sh "docker login -u praveenhema -p ${dockerHubPwd}"
                }
                
                sh "docker push praveenhema/hemasreeapp:${DOCKER_TAG} "
            }
        }
    }
}
def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}
