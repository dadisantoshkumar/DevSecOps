pipeline {
    agent any
    tools {
      maven 'maven3.6.3'
      }
    stages {
        stage ('CleanWorkspace') {
            steps {
              cleanWs()
              }
           }
        stage ('initialize') {
            steps {

                sh '''

                export MAVEN_HOME=/usr/local/maven3.6.3
                export M2_HOME=$MAVEN_HOME/bin
                export PATH=$PATH:$M2_HOME

                '''

            }
        }

        stage ('Check-git-Scerets') {

            steps {

               sh 'docker pull gesellix/trufflehog'
               sh 'docker run gesellix/trufflehog --json https://github.com/dadisantoshkumar/devsecops.git > trufflehog '
               sh 'cat trufflehog'
            }

        }

         stage ('Defectdozo') {
            steps {
            sh 'git clone https://github.com/DefectDojo/django-DefectDojo.git'
            sh 'cd /var/lib/jenkins/workspace/DevSecOps/django-DefectDojo'
            dir("/var/lib/jenkins/workspace/DevSecOps/django-DefectDojo") {
            sh 'pwd'
            sh 'docker-compose build'
            sh 'docker-compose up'
            }
            }
        }

        stage ('build') {
            steps {
            sh 'cd ..'
            sh 'mvn clean install'
            }
        }
   
        stage ('Deploy-to-tomcat') {
        
              steps {
              
              sshagent(['tomcat']) {

                  sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/DevSecOps/target/WebApp.war ubuntu@18.191.247.216:/opt/apache-tomcat-8.5.50/webapps/WebApp.war'

        }

        }

        }

       }


     } 
