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
               sh 'mvn clean'
            }
        }

        stage('Test')
        {
            steps{
                sh 'mvn test'
            }
        }

        stage('Deploy')
        {
            steps{
                
                sshPublisher(publishers: [sshPublisherDesc(configName: 'client', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'java -jar hello-0.0.1-SNAPSHOT.jar &', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'hello-0.0.1-SNAPSHOT.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }

        }
    }
}
