pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent'
            defaultContainer 'jnlp'
        }
    }
    stages {
        stage('Java Check') {
            steps {
                sh 'java -version'
            }
        }
    }
}


