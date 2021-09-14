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
                steps{
                    
                    echo '  data'
                    }
                // Some code that creates that data object
                // data is an array of maps
              
            }

            stage ('Build') {
                // steps {
                //     def stepsForParallel = [:]
                //     data.each { d ->
                //         // name is a key in the data map
                //         stepsForParallel["${d['name']}"] = {
                            
                //                 stage("${d['name']}") {
                //                     stepsForParallel[execDownStreamJob("DownStreamJobName", d)] = {
                //                         println("Executing DownstreamJob")
                //                     }
                //                 }
                //             }
                //         }
                //     }
                //     parallel stepsForParallel
                // }
                    script {
        def stepsForParallel = data.collectEntries{ d ->
            ["${d.name}", 
                {
                    stage("${d.name}") {
                        println "DownstreamJob ${d.name} start")
                        execDownStreamJob("DownStreamJobName", d)
                        println "DownstreamJob ${d.name} end")
                    }
                }
            ]
        }
        parallel stepsForParallel
    }
            }

        }
    