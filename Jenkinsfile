node {
    stage('SCM') {
        checkout scm
    }
          stage('SonarQube Analysis') {
        withSonarQubeEnv() {
          sh "mvn clean verify sonar:sonar -Dsonar.projectKey=spring-boot-dockerizeh -Dsonar.projectName='spring-boot-dockerize'"
        }
      }    
        
    stage('Maven_Build') {
        //first changes
        // sh 'rm -rf target'
        sh 'mvn package'
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
