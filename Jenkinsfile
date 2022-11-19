pipeline {
 agent any
 environment {
  DOCKER_TAG= getDockerTag ()
}
 stages {
  stage ("download git code") {
   steps{
    sh "credentialsId: 'github' 
}
 }

  stage ("create image") {

   steps{
    sh "docker build -t rvnjssss/nodeapp2:${DOCKER_TAG} ."
   
}
}
  stage ("docker push")
{
   steps {

    sh "docker login -u rvnjssss -p ${dockerhubPwd}"
    sh "docker push rvnjssss/nodeapp2:${DOCKER_TAG}"

}
}
}
}
}

def getDockerTag() {

 def tag = sh script: 'git rev-parse HEAD', returnStdout: true
 return tag
}
