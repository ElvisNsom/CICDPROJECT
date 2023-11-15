


pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                script {
                    try {
                        git 'https://github.com/mankinimbom/maven.git'
                    }catch (Exception e) {
                        mail bcc: '', body: 'jenkins was unable to download the code from the repository', cc: 'nkainelvis@gmail.com', from: '', replyTo: '', subject: 'git clone failed', to: 'nkainelvis@gmail.com'
                        error('git checkout failed')
                    }
                }
                
            }
        }

        stage('Build') {
            steps {
                script {
                    try {
                        sh 'mvn package'
                    }catch (Exception e) {
                        mail bcc: '', body: 'jenkins was unable to download the code from the repository', cc: 'nkainelvis@gmail.com', from: '', replyTo: '', subject: 'git clone failed', to: 'nkainelvis@gmail.com'
                        error('maven build failed')
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    try {
                        sh 'mvn test'
                    }catch (Exception e) {
                        mail bcc: '', body: 'jenkins was unable to download the code from the repository', cc: 'nkainelvis@gmail.com', from: '', replyTo: '', subject: 'git clone failed', to: 'nkainelvis@gmail.com'
                        error('Tests failed')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    try {
                        deploy adapters: [tomcat9(credentialsId: '87d4983a-8c65-452a-b712-4c2e16b3510e', path: '', url: 'http://172.20.122.164:8085')], contextPath: 'Demo', war: '**/*.war'
                    }catch (Exception e) {
                        mail bcc: '', body: 'jenkins was unable to download the code from the repository', cc: 'nkainelvis@gmail.com', from: '', replyTo: '', subject: 'git clone failed', to: 'nkainelvis@gmail.com'
                        error('deployment failed')
                    }
                }
            }
        }
    }
}  
