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
                sh 'scp -o StrictHostKeyChecking=no /home/nandhu1/.jenkins/workspace/flipkart/target/flipkart.war nandhu@192.168.56.105:/home/nandhu/apache-tomcat-8.5.73/webapps/
                sh 'ssh nandhu@192.168.56.104 "/home/nandhu/apache-tomcat-8.5.73/bin/startup.sh"'
              }      
           }       
       }
    }
   }
