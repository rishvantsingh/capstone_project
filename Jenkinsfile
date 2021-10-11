pipeline{
    agent any

    tools{
        maven 'MAVEN'
        jdk   'JDK'
    }

    stages{

       stage('cleanup')
        
        {
            steps{
                cleanWs()
            }
        }

        stage('Test')
        {
            steps{
                sh 'mvn clean test'
            }
        }
    }
}
