pipeline {
     agent any
     stages {
         stage('Lint HTML') {
              steps {
                  echo 'hello world'   
                  script {tidy -q -e index.html}
              }
         }         
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-benny')
                  }
              }
         }
     }
}
