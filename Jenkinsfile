pipeline {
    agent any
    tools {nodejs "node17"}
    environment {
        NODE_ENV='produciton'
    }

    stages {
        stage('source') {
            steps {
                git branch: 'jenkins', url: 'https://github.com/htetzayan/jenkins-codebuild.git'
        
            }
        }
        
          stage('build') {
              environment{
                  NODE_ENV='staging'
              }
            steps {
                echo NODE_ENV
                withCredentials([string(credentialsId: 'ef62967d-700d-4994-b2b1-94662175fc40', variable: 'secvar')]) {
                    // some block
                    echo secvar
                  }
                sh 'npm install'
        
            }
        }
          stage('artifact') {
            steps {
                archiveArtifacts artifacts: '**', followSymlinks: false
        
            }
        }
    
    }
}
