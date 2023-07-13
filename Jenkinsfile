pipeline {
    agent any

    stages {
        stage('Clone') { 
           steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/golfcnt19/my-app']])
            }
        }
        stage('Build') { 
            steps {
               bat "docker build -t my-app/angular-app:latest ${workspace}"
            }
        }
         stage('Deploy') { 
            steps {
                bat "docker run -d -it -p 80:80/tcp --name angular-app my-app/angular-app:latest"
               echo "Success"
            }
        }
    }
}