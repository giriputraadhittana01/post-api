pipeline {
    agent any
    stages('Prepare Code') {
        steps {
            sh 'git clone https://github.com/giriputraadhittana01/post-api.git'
        }
    }
    stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'nodeJS v16.14.0') {
                    sh 'npm install'
                }
            }
        }
    stages('Test') {
        steps {
            sh "npm test"
        }
    }
    stages('Deploy') {
        steps {
            withCredentials([string(credentialsId: 'heroku-token', variable: 'TOKEN')]) {
                sh 'git push https://:${TOKEN}@git.heroku.com/web-post-api.git HEAD:master'
            }
        }
    }
}