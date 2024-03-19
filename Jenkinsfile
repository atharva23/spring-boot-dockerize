node {
    stage('SCM') {
        checkout scm
    }
    stage('Maven_Build') {
        // sh 'rm -rf target'
        sh 'mvn package'
    }
      stage('SonarQube Analysis') {
        def mvn = tool 'Default Maven';
        withSonarQubeEnv() {
          sh "mvn clean verify sonar:sonar -Dsonar.projectKey=test -Dsonar.projectName='test'"
        }
      }    
        
    stage('Docker_Build') {            
            // Build Docker image
            sh 'docker build -t spring-boot-docker.jar .'            
    }
    stage('Run_Docker_Container') {            
            // Run Docker container
            sh 'docker run -d -p 9090:8080 spring-boot-docker.jar'            
    }    
}
