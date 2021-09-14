pipeline {
    agent any
    stages {
        stage ('clone the repo') {
            steps {
                git clone 'https://github.com/wesalEldsokey/hello-world'
            }
        }
        
        
        
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