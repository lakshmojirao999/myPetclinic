
node {
 checkout scm
 def dockerImage
   stage('Build image') {
    dockerImage = docker.build("lakshmojirao999/petclinic")

}
 

   stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'docker') {

           dockerImage.push('1')

           dockerImage.run('-p 8484:8080')
       }
   }
}
