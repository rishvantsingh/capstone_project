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

        stage('Build'){
            steps{
              sh 'mvn clean compile pom.xml'
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