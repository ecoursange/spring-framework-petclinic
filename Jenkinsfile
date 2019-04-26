pipeline {
    agent any

    tools {
        maven "maven 3.6"
        sonar "SonarQube"
    }

    stages {
        stage('Build') {
           steps{
              // Run the maven build
              sh "mvn clean package"
           }
        }
         stage('Checkstyle') {
           steps{
              // Run the maven build with checkstyle
              sh "mvn clean package checkstyle:checkstyle"
           }
        }
        stage('SonarQube Analysis') {
           steps{
               withSonarQubeEnv {
                    // Run the maven build with sonar
                    sh "clean package sonar:sonar -Dsonar.host_url=$SONAR_HOST_URL "
                }
            }
        }
    }
}
