pipeline{

    agent any

    tools { 

        maven 'maven3'

    }

    stages

       {

            stage("clean")

            {

                steps{

                    sh "mvn clean"

                }

            }

            stage("Build")

            {

                steps{

                    sh "mvn compile"

                }

                

            }
           stage('Parallel and archiving') {
          parallel {

            stage('Test'){
              steps {
               sh 'mvn test'
              }
            }
             stage('Archiving') {
              steps {
               sh 'echo "Artifact" > test1.txt'
                archiveArtifacts artifacts: 'test1.txt'
                }
              }
          }
        }
    }
    post {
           success{
                emailext to: "akash.kumar@knoldus.com",
                subject: "Test Email Sucess",
                body: "Test Success"
            }

            failure{
                emailext to: "akash.kumar@knoldus.com",
                subject: "Test Email Failure",
                body: "Test Failure"
            }
        always {
            emailext body: 'abcdedv', subject: 'abcd', to: 'mansi.wisethink@gmail.com'
           }
    }
}
