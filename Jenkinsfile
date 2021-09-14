// pipeline {
//     agent any
//     stages {
      

        
        
//         stage('Build') {
//             steps {
                
//                 echo 'building the application'
//             }
//         }
//         stage('Test') {
//             steps {
              
//                 echo 'test the application'
//             }
      
//         }
//         stage('Deploy') {
//             steps {
//                 echo 'deploy the application '
//             }
//         }
//     }
// }
    pipeline {

        agent any

        stages {

            stage ('Prepare Data') {
                // Some code that creates that data object
                // data is an array of maps
              echo '  data'
            }

            stage ('Build') {
                script {
                    def stepsForParallel = [:]
                    data.each { d ->
                        // name is a key in the data map
                        stepsForParallel["${d['name']}"] = {
                            
                                stage("${d['name']}") {
                                    stepsForParallel[execDownStreamJob("DownStreamJobName", d)] = {
                                        println("Executing DownstreamJob")
                                    }
                                }
                            }
                        }
                    }
                    parallel stepsForParallel
                }
            }

        }
    