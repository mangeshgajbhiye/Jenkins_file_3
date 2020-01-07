pipeline {

   agent any

   triggers {
     pollscm 'H/2 * * * 1-5'
   }

   parameter {

       choice choices:['QA','PreUser','Radhe'],description:'This is parameter project',name:'ENVIRONMENT'
   }

   stages {

       stage ('Checkout') {

           steps {
               checkout scm
           }
       
       }
       stage ('Build') {
              steps {
                  sh '/home/mangesh/Software/apache-maven-3.6.1/bin/mvn install'
              }
       }
       stage ('Deployment') {
             steps {
                 script {

                    if (ENVIRONMENT == 'QA'){
                       sh 'sshpass -p "QAserver" scp target/Bhavani.war QAserver@172.17.0.2:/home/QAserver/Teast/parameter'
                       sh 'echo "Hi My name is Mangesh"'
                    } else if (ENVIRONMENT == 'Preuser'){
                       sh 'sshpass -p "PreUser" scp target/Bhavani.war PreUser@172.17.0.3:/home/PreUser/Pragati/Parameter'
                       sh 'echo Hi we are in PreUser'
                      }
                  }
 
             }
       }

   }
   



}
