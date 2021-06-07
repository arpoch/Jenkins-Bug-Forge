pipeline {
    agent any
    stages {
       
        stage('Tag'){
            steps {
                sh 'echo adding tag'
                withCredentials([GitUsernamePassword('9f491dfd-135b-4c09-a731-42735ff6fa9a')]) {
                     sh 'git push origin :refs/tags/v2.0'                
                }                
                git branch: 'mavenTest', changelog: false, credentialsId: '9f491dfd-135b-4c09-a731-42735ff6fa9a', poll: false, url: 'https://github.com/arpoch/Jenkins-Bug-Forge.git'
                sh 'git tag -a v2.0 -m "gitUsernamePassword-TestCase-2"'
            }
            post {
                success {
                    withCredentials([GitUsernamePassword('9f491dfd-135b-4c09-a731-42735ff6fa9a')]) {
                     sh 'git push origin v2.0'                
                    }
                     sh 'echo Tag added successfully.'
                }
            }
        }        
        stage('Push') {
            steps{
                withCredentials([GitUsernamePassword('9f491dfd-135b-4c09-a731-42735ff6fa9a')]) {
                    sh 'git push origin mavenTest'
                }
            }
            post {
                success {
                    sh 'echo push successfully.'
                }
            }
        }
    }
}



