pipeline{
    agent {
        label 'slave1'
    }
    tools{
        maven 'MAVEN'
        jdk   'JAVA'
    }

    stages{

       stage('cleanup')
        
        {
            steps{
                sh 'mvn clean'
            }
        }

        stage('Build'){
            steps{
              sh 'mvn clean compile'
            }


        }
        stage('Test')
        {
            steps{
                sh 'mvn clean test'
            }
        }
    }
    
    post {
        always{
        
            $PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

            Check console output at $BUILD_URL to view the results.
            
        }
    }
}
