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
        stage('DOCKER BUILD IMAGE'){
            steps{
                sh "docker build . -t praveenhema/hemasreeapp:${DOCKER_TAG} "
            }
        }
    }
}
def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}
