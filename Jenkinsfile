pipeline {
    agent any

    stages {
        stage ('initialize') {
            steps {

                sh'''

                echo $MAVEN_HOME

                '''

            }
        }

        stage ('build') {
            sh 'mvn clean install'
        }
    }

}
