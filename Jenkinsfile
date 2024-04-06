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
               
        }
}
