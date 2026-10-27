pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sindhuja-siva-vasuki/static-website.git'
            }
        }

        stage('Validate') {
            steps {
                sh 'test -f index.html'
                echo 'Validation Successful'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo cp index.html /var/www/html/index.html
                '''
            }
        }
    }
}
