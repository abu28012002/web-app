pipeline {
    agent any

    stages {
        stage('Code') {
            steps {
              git 'https://github.com/abu28012002/web-app.git'
            }
        }
        stage('code-build') {
            steps {
                 sh "mvn clean package"
            }
        }
     
    }
}
