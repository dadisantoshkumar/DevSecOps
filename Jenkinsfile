pipeline {
  agent any
  stages {
       stage ('DAST') {
         steps {
          sh 'docker run -t owasp/zap2docker-stable zap-baseline.py -t https://flpnwc-jswaw8q61t.dispatcher.eu3.hana.ondemand.com/sites?siteId=59265e60-5c15-4ece-bc09-2fab43e63cdb#Shell-home || true'
        }
      }
       }
  }

