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
                                
                                     deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.110.54.77:8080')], contextPath: null, war: '**/*.war'
                                
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
