pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: '']]) 
            }
        }
        stage('build'){
            steps{
               sh 'mvn package'
             }
        }
        stage('deploy to tomcat'){
            steps{
               deploy adapters: [tomcat9(credentialsId: '42e27830-4da3-41a5-8022-37ed1eb0c5a8', path: '', url: 'http://16.16.193.126:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
