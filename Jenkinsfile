pipeline {
  agent any
  environment {
    DOCKER_TAG= getDockerTag ()
 }
   stages {
   stage ("download git code") {
     steps{
       git branch: 'main', credentialsId: 'gitcredentials', url: 'https://github.com/midathanasiva/dockerpush'
        }
    }

   stage ("create image") {

      steps{
          sh "docker build . -t rvnjssss/nodeapp2:${DOCKER_TAG}"
   
}
}
   stage ("docker push")
  {
      steps {
                  withCredentials([string(credentialsId: 'jenkinspasswordonly', variable: 'passfordocker')]) {
                    sh "docker login -u rvnjssss -p ${passfordocker}"
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
