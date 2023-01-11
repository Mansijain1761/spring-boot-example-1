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
                emailext to: "mansi.jain@knoldus.com",
                subject: "Test Email Sucess",
                body: "Test Success"
            }

            failure{
                emailext to: "mansi.jain@knoldus.com",
                subject: "Test Email Failure",
                body: "Test Failure"
            }
        always {
            emailext body: 'abcdedve', subject: 'abcd', to: "mansi.jain@knoldus.com"
           }
    }
}
