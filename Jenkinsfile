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
                              cd /var/lib/jenkins/workspace/Java_Deployment_23_11_2022/helloworld/1project
                              mvn clean install
                              echo "Build is successful"
                              '''
                              }
                           }
                        stage ('Deploy to tomcat server') {
                                steps{
                                     deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.108.235.40:8080')], contextPath: null, war: '**/*.war'
                         }
                       stage ('DEPLOY') {
                              steps {
                              sh '''
                              #!/bin/bash
                              sudo cp /var/lib/jenkins/workspace/Java_Deployment_23_11_2022/helloworld/1project/target/hello-world-war-1.0.0.war /opt/tomcat/webapps/
                              sudo systemctl start tomcat
                              echo "Deployed war file to tomcat successfully"
                              '''
                              }  
                       }
                        stage ('TEST') {
                              steps {
                              sh '''
                              cd /var/lib/jenkins/workspace/Java_Deployment_23_11_2022/helloworld/1project
                              mvn test
                              echo "Tested successfully"
                              '''
                              } 
                      }
                
                }
    }
