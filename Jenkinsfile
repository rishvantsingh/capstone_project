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

        stage('Test')
        {
            steps{
                sh 'mvn test'
            }
        }
       
       stage('Package'){
          steps{
             sh 'mvn package'
          }
       }

        stage('Deploy')
        {
            steps{
                
               sshPublisher(publishers: [sshPublisherDesc(configName: 'client', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''cd target
java -jar *.jar &''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
            }

        }
    }
   post {
        always{
        
          emailext body: '''$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

Check console output at $BUILD_URL to view the results.''', subject: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!', to: 'rishivantsingh9717@gmail.com'
        }
        
    }
}
