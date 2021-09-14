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

        agent {
            label "l1" && "l2"
        }

        stages {

            stage ('Prepare Data') {
                // Some code that creates that data object
                // data is an array of maps
                data
            }

            stage ('Build') {
                script {
                    def stepsForParallel = [:]
                    data.each { d ->
                        // name is a key in the data map
                        stepsForParallel["${d['name']}"] = {
                            node {
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
    }
}