
node {
 checkout scm
 def dockerImage
   stage('Build image') {
    dockerImage = docker.build("lavanyapatil/petclinic:new")
   }
   stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'docker') {

           dockerImage.push('1')

           dockerImage.run('-p 8485:8080')
       }
   }
}
