node

  {
        def mavenHome = tool name:"maven3.8.1"
        
        properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
        
        stage('checkout')
        {
        git credentialsId: '02f79dd1-790d-4d7c-8317-98a004fcabb8', url: 'https://github.com/Fasi326/maven-web-application.git'
        }
        
        stage('build')
        {
            sh "${mavenHome}/bin/mvn clean package"
        }
        
      /*   stage('sonar report')
        {
            sh "${mavenHome}/bin/mvn sonar:sonar"
        }
        
         stage('storing artifact')
        {
            sh "${mavenHome}/bin/mvn deploy"
        }
        
        stage('deploy application into tomcat server')
        {
            sshagent(['122af1f3-1ffe-4d16-909e-47a483fa89eb'])
            {
             sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.126.99.147://opt/apache-tomcat-9.0.45/webapps/"
            }   
        }  */
        
        stage('sending notification')
        {
         mail bcc: '', body: '''Hi Fasi,

     please go through the  "$BUILD_URL" and verify.

thanks''', cc: 'rehamanyasin@gmail.com', from: '', replyTo: '', subject: 'job "$JOB_NAME" with "$BUILD_NUMBER" is waiting for the input', to: 'fasirehaman@gmail.com'
        }
    }
