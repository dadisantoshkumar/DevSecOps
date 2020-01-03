pipeline {
    agent any
    tools {
      maven 'maven3.6.3'
      }
    stages {
        stage ('initialize') {
            steps {

                sh '''

                export MAVEN_HOME=/usr/local/maven3.6.3
                export M2_HOME=$MAVEN_HOME/bin
                export PATH=$PATH:$M2_HOME

                '''

            }
        }

        stage ('build') {
            steps {
            sh 'mvn clean install'
            }
        }
   
        stage ('Deploy-to-tomcat') {
        
              steps {
              
              sshagent(['tomcat']) {

                  sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/DevSecOps/target/WebApp.war ubuntu@3.16.158.245:/apache-tomcat-8.5.50/webapps/WebApp.war'

        }

        }

        }

       }


     } 
