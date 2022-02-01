pipeline {
    agent any
    tools {
    maven 'My_Maven'
    }
  stages {
    stage('Git Checkout') {
      steps {
        git branch: 'main',
          credentialsId:'9ceac5cd-0a88-423c-b03d-022de810ca95',
          url: 'https://github.com/MS-cloudtechner/Final.git'
       sh 'echo Git Checkout complete'
      }
    }
        stage('compile') {
            steps {
                sh 'mvn clean install'
                sh 'echo compile completed'
            }
        }
       stage('package') {
            steps {
                sh 'mvn package'
            }
        }
       stage('Unit test') {
            steps {
                sh 'mvn test'
            }
        }
      stage('Deployment') {
            steps {
                sh 'cp /root/.jenkins/workspace/Java-pipeline/target/*.war /opt/tomcat/webapps'
            }
        }
   stage('installing webapp') {
            steps {
                 sh '/opt/tomcat/bin/startup.sh'
            }
        }  
  }
}
