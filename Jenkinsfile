
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sindhuja-siva-vasuki/static-website.git'
            }
        }

        stage('Validate') {
            steps {
                sh '''
                    test -s index.html
                    grep -q "CI/CD Pipeline Success" index.html
                '''
                echo 'Validation Successful'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo install -m 644 index.html /var/www/html/index.html
                    sudo nginx -t
                    sudo systemctl reload nginx
                    echo "Deployment Successful"
                '''
            }
        }
    }
}
