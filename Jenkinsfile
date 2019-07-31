node {
   
   stage('Code Checkout') { 
     git credentialsId: 'git', url: 'https://github.com/ChiragBarsaiya/maven_apps.git'
     
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
   stage('Sonar CodeAnalysis') {
     withMaven(jdk: 'JDKv8', maven: 'Maven') {
        sh 'mvn sonar:sonar -Dsonar.projectKey=maven-examples -Dsonar.organization=chiragbarsaiya -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=cd881660badd69bf040c5ddae90f4a4795fd3db2'   }  
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
