pipeline {
    agent any

    stages {
      
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'mvn package -DskipTests'
                    } else {
                        bat 'mvn package'
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
