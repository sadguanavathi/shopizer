pipeline{
  agent any
  triggers { pollSCM('H */4 * * *') }
  parameters { string(name: 'mavengoal', defaultValue: 'package', description: 'build the code') }
  stages{
     stage('vcs'){
        steps{
          git url: "https://github.com/sadguanavathi/shopizer.git",
              branch: "dev"
            }
        }
        stage('build'){
         steps{
            sh "mvn ${params.mavengoal}"

             }
         }
         stage('archiveartifactes'){
            steps{
                archive includes: '**/target/*.jar'
            }
         }
         stage('unit test results'){
            steps{
                junit testResults: '**/target/surefire-reports/*.xml'
            }
         }
    }
}

