node {
   
   stage('Code Checkout') { 
     git credentialsId: 'git', url: 'https://github.com/ChiragBarsaiya/maven-examples.git'
     
    }
   stage('Build') {
    withMaven(jdk: 'JDKv8', maven: 'Maven') {
      sh 'mvn clean compile'
      }
    }
   stage('Unit Test run') {
    withMaven(jdk: 'JDKv8', maven: 'Maven') {
     sh 'mvn test'
      } 
    }
   
   withSonarQubeEnv(credentialsId: 'SonarQube') {
    withMaven(jdk: 'JDKv8', maven: 'Maven') {
    sh 'mvn sonar:sonar' 
      }
    }
  stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
    }
   stage('Package to Jfrog') {
    withMaven(jdk: 'JDKv8', maven: 'Maven') {
     sh 'mvn package'
      }
    }
   
   stage('Deploy to Dev') {
     
    }
   stage('Automation Testing') {
     
    }
   stage('Deploy to Test') {
     
    }
   stage('Smoke Testing') {
     
    }
   stage('Deploy to Prod') {
    
    }
   stage('Acceptance Testing') {
     
    }
}
