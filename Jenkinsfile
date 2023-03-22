pipeline {
    agent {
        label {
            label 'dev'
            customWorkspace "/opt/go-app"
        }
    }
    environment {
        Go111MODULE='on'
    }
    stages {
        stage('Build Dev') {
            steps {
                sh 'git pull https://github.com/ybkuroki/go-webapp-sample.git'
            }
        }
    
  
        stage('Test Dev') {
            steps {
                 sh 'go test ./...'
            }
        }
    
        stage('Deploy Dev') {
            steps {
                script {
                    withEnv ( ['JENKINS_NODE_COOKIE=do_not_kill'] ) {
                    sh 'go run main.go &'
                    }
                }
            }
        }
    }
}
