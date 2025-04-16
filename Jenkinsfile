pipeline {
    agent any

   stages {
        stage('Checkout') {
            steps {
               git branch: 'main', credentialsId: '0e4aedd0-acd4-4596-acd9-a8225012a929', url: 'git@github.com:Zakir1109022/OSTAD-Assignment-module-3.git'
            }
        }
        
         stage('Install Dependencies') {
            steps {
              sh 'npm install'
            }
        }
        
         stage('Run Tests') {
            steps {
                script {
                    try {
                        def testOutput = sh(script: 'npm run check', returnStdout: true).trim()
                        echo "Test Output:\n${testOutput}"
                    } catch (Exception e) {
                        echo "Error running tests: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        throw e // Fail the build
                    }
                }
            }
        }
        
    }
}
