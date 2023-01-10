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

            stage("TEST")

            {

                steps{

                    sh "mvn test"

                }

            }

            stage("package")

            {

                steps{

                    sh "mvn package"

                }

            }
               stages {
        stage('Ok') {
            steps {
                echo "Ok"
            }
        }
    }
    post {
        always {
            emailext body: 'abcd', subject: 'abcd', to: 'mansi.wisethink@gmail.com'
           }
    }

        

    }

 

}
