pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/SwapnilDhawad/jenkins-example'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MavenAWS') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MavenAWS') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'MavenAWS') {
                    sh 'mvn install'
                }
            }
        }

         stage ('deploy to tomcat') {
             steps {
                 sshagent(['ssh-pipline']) {
                 sh 'scp -o StrictHostKeyChecking=no target/*.jar ec2-user@35.177.130.68:/var/lib/tomcat/webapps/'
      }
             }
   }
}
}
