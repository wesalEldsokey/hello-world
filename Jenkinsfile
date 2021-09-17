pipeline {
agent any 
    tools {
    maven 'maven-3.8' 
    }
    
    
    stages {
    
        stage ('code building') {
            steps {
                script{
                    echo '55555555'
             //     sh 'mvn package'
                }
            }
          
        }
        stage ('code testing') {
            steps {
                script {
                echo 'testing the code'
                }
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    echo "Building Docker image"
                    withCredentials([usernamePassword (credentialsId: 'wesal-docker' , passwordVariable: 'PASS', username: 'USER')])
                    sh 'docker build -t wesalEldsokey/hello-world .'
                    sh "echo $PASS | docker loging -u $USER --password-stdin"
                    sh 'docker push wesalEldsokey/hello-world'
                }
            }
        
        }
        stage ('Delpoying') {
            steps {
                script {
                 echo 'Deploying the application '
                }
            }
        }
        
    }

}
