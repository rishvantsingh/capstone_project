pipeline{
    agent any

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
}
