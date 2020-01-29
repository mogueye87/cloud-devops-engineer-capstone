pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Hello world'
                sh 'ls -lah'
            }
        }
        stage(‘Lint HTML’) {
            steps {
                sh ‘tidy -q -e *.html’
            }
        }
   }
}