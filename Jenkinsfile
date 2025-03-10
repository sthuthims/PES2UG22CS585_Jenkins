pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'g++ -o PES2UG22CS585 hello.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS585-edit'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'git config --global user.name "sthuthi"'
                    sh 'git config --global user.email "sthuthimjalu@gmail.com"'
                    sh 'git checkout -B main origin/main'
                    sh 'git add -A'
                    sh 'git commit -m "Added hello.cpp file" || echo "No changes to commit"'
                }
            }
        }

        stage('Post Actions') {
            steps {
                echo "Pipeline completed successfully"
            }
        }
    }

    post {
        success {
            echo "Build and deployment successful!"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}
