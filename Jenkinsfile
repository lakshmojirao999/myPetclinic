
node {
 checkout scm
 def dockerImage
   stage('Build image') {
    dockerImage = docker.build("lavanyapatil/pet")
   }
   stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'docker') {

           dockerImage.push('1')
       }
   }
}
