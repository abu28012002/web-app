pipeline {
    agent {
        label 'slave1'
    }

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
       stage('artifact'){
           steps{
               nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb-8.6.5.war', type: '.war']], credentialsId: 'admin', groupId: 'in.javahome', nexusUrl: '44.212.62.229:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'nexus', version: '8.6.5'
           }
       }  
        stage('deploy'){
            steps{deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://3.87.199.154:8080')], contextPath: 'builds', war: 'target/*.war'
              } 
         }
post{
    success{
        echo "hello"
    }
    }

}
