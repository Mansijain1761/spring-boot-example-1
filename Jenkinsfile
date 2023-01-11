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
           stage('Hello print') {
            steps {
                echo "Hello world"
                    }
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
                emailext to: "onlinesuitparadise@gmail.com",
                subject: "Test Email Sucess",
                body: "Test Success"
            }

            failure{
                emailext to: "onlinesuitparadise@gmail.com",
                subject: "Test Email Failure",
                body: "Test Failure"
            }
        always {
            emailext body:"demo", subject: "demo", to: "onlinesuitparadise@gmail.com"
           }
    }
}
