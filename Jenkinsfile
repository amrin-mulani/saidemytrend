pipeline {
    agent any
    environment{
        PATH="/opt/maven/bin:$PATH"
    }
          stage('Build') {
            steps {
                  sh "mvn clean deploy"
            }
        }

      stages {
        stage('SonarQube analysis') {
            environment{
                 scannerHome = tool 'amrin-sonarqube-scanner'
            }
        }
         
        
            steps {
                  withsonarQubeEnv('amrin-sonarqube-server'){
                   sh "${scannerHome}/bin/sonar-scanner"
            }
        }
      }
}
 
