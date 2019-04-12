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
           sh 'mvn clean package'
           junit '**/target/surefire-reports/TEST-*.xml'
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
