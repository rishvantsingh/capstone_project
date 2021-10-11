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
