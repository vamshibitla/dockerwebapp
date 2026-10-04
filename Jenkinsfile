node {
  stage('SCM') {
    checkout scm
  }
  stage ("build") {
            steps {
                sh 'mvn clean install'
            }
        }

  
  stage('SonarQube Analysis') {
    def mvn = tool 'mymaven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=myproject-key -Dsonar.projectName='myproject'"
    }
  }
}
