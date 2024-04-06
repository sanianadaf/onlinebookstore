pipeline {  
    agent any  
        stages {  
       	    stage("git_checkout") {  
           	    steps {  
              	    echo "cloning repository" 
              	    echo "repo cloned successfully"  
              	    }  
         	    } 
            stage('Checkout') {
                      steps {
                                  sh 'echo passed'
                                  git branch: 'master', url: 'https://github.com/Seema21-sm/onlinebookstore.git'
                              }
            }
                stage('Build and Test') {
                          steps {
                                      sh 'ls -ltr'
                                      // build the project and create a JAR file
                                      sh ' mvn clean package'
                          }
                }
                stage('Static Code Analysis') {
                          environment {
                                      SONAR_URL = "
                              http://13.232.6.130:9000/"
                                  }
                          steps {
                                      withCredentials([string(credentialsId: 'sonarqube', variable: 'SONAR_AUTH_TOKEN')]) {
                                                    sh 'cd spring-boot-app && mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
                                      }
                          }
        }
}
