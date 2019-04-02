pipeline {
    agent any 
        
        // docker {
        //     image 'node:6-alpine'
        //     args '-p 3000:3000'
        // }
    
    // This creates a variable CI with the value of true.
    // This can be now accessed in all steps of the pipeline
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
