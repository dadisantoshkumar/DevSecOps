pipeline {
    agent any
    tools {
      maven 'maven3.6.3'

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
    }

}
