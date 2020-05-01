pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
      }
    }
  stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    } 
  stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-west-2', credentials: 'cabbf8ea-ae06-4bc6-8f2c-8049e15771e8') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'ian-jenkins-pipeline')
        }
      }
    }       
  
  }
}    