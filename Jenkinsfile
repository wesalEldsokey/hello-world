// declare our vars outside the pipeline
def tests = [:]
def files

pipeline {
    agent any
    stages {
        stage('1') {
            steps {
                script {
                    // we've declared the variable, now we give it the values
                    files = findFiles(glob: '**/html/*.html')
                    // Loop through them
                    files.each { f ->
                        // add each object from the 'files' loop to the 'tests' array
                        tests[f] = {
                            // we're already in the script{} block, so do our advanced stuff here
                            echo f.toString()
                        }
                    }
                    // Still within the 'Script' block, run the parallel array object
                    parallel tests
                }
            }
        }       
    }
}
