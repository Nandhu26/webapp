pipeline {
    agent any
    tools {
       maven 'maven'
    }
    stages {
      stage('Build'){
        steps{
          sh 'mvn clean package'
        }
      }
    stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sshpass -p "nandhu@123" scp /home/nandhu1/.jenkins/workspace/flipkart/target/flipkart.war nandhu@192.168.56.104:/home/nandhu/apache-tomcat-8.5.73/webapps/
                 sshpass -p "nandhu@123" ssh nandhu@192.168.56.104 "/home/nandhu/apache-tomcat-8.5.73/bin/startup.sh"
              }      
           }       
       }
    }
   }
