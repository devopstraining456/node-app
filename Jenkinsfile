pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages{
        stage('Build Docker Image'){
            steps{
                sh "docker build -t kubernetes8/nodeapp . "
            }
}
            stage('DockerHub Push'){
  withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPws')]) {
                    sh "docker login -u kubernetes8 -p ${dockerHubPwd}"
                    sh "docker push kubernetes8/nodeapp:${DOCKER_TAG}""
      }
    }
 }

}



  }
def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}
