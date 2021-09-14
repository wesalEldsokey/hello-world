pipeline {
    agent any
    stages {
      
        
        
        
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
                echo 'building the application'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo 'test the application'
            }
      
        }
        stage('Deploy') {
            steps {
                echo 'deploy the application '
            }
        }
    }
}