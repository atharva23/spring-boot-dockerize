node {
    stage('SCM') {
        checkout scm
    }
    stage('Maven_Build') {
        // sh 'rm -rf target'
        sh 'mvn package'
    }
}
