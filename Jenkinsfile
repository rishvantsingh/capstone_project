pipeline{
    agent{
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

        stage('Test')
        {
            steps{
                sh 'mvn test'
            }
        }
    }
}
