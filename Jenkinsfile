pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Install') {
            when {
                branch 'development'
            }
            steps {
                sh 'mvn install'
            }
        }
        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                // Add deployment steps here (e.g., deploy war file to a server)
                echo "deploy stage"
           deploy adapters: [tomcat9 (
                   credentialsId: 'deployer',
                   path: '',
                   url: 'http://52.170.151.187:8088/'
               )],
               contextPath: 'Demo',
               onFailure: 'false',
               war: '**/*.war'

            }
        }
    }
}
