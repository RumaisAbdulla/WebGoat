pipeline {
    agent any

    stages {
      
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'mvn --version'
                    } else {
                        bat 'mvn package -DskipTests'
                    }
                }
            }
        }
        
        stage('SonarQube Analysis') {
            steps{
                script{
                     def scannerHome = tool 'sonar-local';
                     withSonarQubeEnv() {
                    bat "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=Webgoatfinal -Dsonar.java.binaries=target/classes"
                    }
                }
            }
        }
    }
}
