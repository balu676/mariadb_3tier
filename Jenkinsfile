pipeline {
    agent any
    options { buildDiscarder(logRotator(numToKeepStr: '10')) }
    
    stages {
        stage('helm version') {
            steps {
                sh 'helm version'
            }
        }
    stage('deploy mariadb') {
            steps {
               sh '''
                   helm upgrade --install devops18-mariadb $WORKSPACE --values $WORKSPACE/createat-mariadb.yaml'''
            }
        }
    stage('verification') {
            steps {
                sh 'kubectl get po -n mariadb '
            }
        }
    
    }
}
