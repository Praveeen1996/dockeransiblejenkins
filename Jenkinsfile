pipeline {
    agent any
    tools {
  maven 'maven-3.9.3'
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
        stage('Maven Build'){
            steps{
                sh "mvn clean package"
            }
        }
    }
}
