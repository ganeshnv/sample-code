pipeline {
   agent any
   stages {
      stage('checkout') {
          steps {
          git 'https://github.com/ganeshnv/sample-code.git'
          }
      }
    
     stage('Build') {
        steps {
           sh 'mvn clean compile'
        }
     }
     stage('Test') {
        steps {
           sh mvn test
           junit '**/target/surefire-reports/TEST-*.xml'
        }
     }
     stage('Package') {
        steps {
           sh 'mvn clean package'
        }  
     } 
    post {
    always {
       mail to: "nv.ganesh93@gmail.com" ,
       body: "Build status ${env.BUILD_URL}",
       subject: "Pilepile Job: ${currentBuild.fullDisplsyName}"
     }
   }
}
