pipeline {
    agent any
    environment {
        AWS_CREDENTIALS_ID = 'aws-credentials'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/78654sri/Employee-Management-Admin-Panel.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to master') {
            steps {
                sh '''
                aws s3 cp target/*.jar s3://my-staging-bucket/
                '''
            }
        }
    }
}
