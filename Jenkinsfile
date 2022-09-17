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
        always {
            emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
        }
    }
}
