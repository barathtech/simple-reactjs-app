 pipeline {
    agent any
    stages {
        stage('build') {
            steps { 
                sh'''apt-get update && apt-get upgrade -y'''
                sh'''apt-get install npm -y'''
                sh'''npm start'''
            }
        }
        stage('Deploy') {
            steps{
              sshagent(credentials : ['barath']) {
              sh 'ssh -o StrictHostKeyChecking=no ubuntu@10.0.0.224'
              sh 'scp -p -r /var/lib/jenkins/workspace/demo ubuntu@10.0.0.224:/var/www/'
              }
            }
        }
    }
}
