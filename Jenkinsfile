pipeline {
        agent any
              
                stages {
                      stage ('CLONE') {
                          steps {
                             git branch: 'main', credentialsId: 'GIT_CRED', url: 'https://github.com/Nishanth1987/My-Java-Deployment.git' 
                          }
                      }
                      
                      stage ('BUILD') {
                          
                              steps {
                              sh '''
                              #!/bin/bash
                              cd /home/jenkins/workspace/Java Deployment_23_11_2022/helloworld/1project
                              mvn clean install
                              echo "Build is successful"
                              '''
                              }
                       }
                       stage ('DEPLOY') {
                              steps {
                              sh '''
                              #!/bin/bash
                              sudo cp /home/jenkins/workspace/Java Deployment_23_11_2022/helloworld/1project/target/hello-world-war-1.0.0.war /opt/tomcat/webapps/
                              sudo systemctl start tomcat
                              echo "Deployed war file to tomcat successfully"
                              '''
                              }  
                       }
                        stage ('TEST') {
                              steps {
                              sh '''
                              cd /home/jenkins/workspace/Java Deployment_23_11_2022/helloworld/1project
                              mvn test
                              echo "Tested successfully"
                              '''
                              } 
                      }
                
                }
    }
