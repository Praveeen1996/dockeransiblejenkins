pipeline {
    agent any
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
    }
}
