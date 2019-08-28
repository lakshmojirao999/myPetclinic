
node {
 checkout scm
 def dockerImage
   stage('Build image') {
    dockerImage = docker.build("zelar/petclinic:latest")
   }
   stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
           dockerImage.push('push lavanyapatil/pet:latest' )
       }
   }
}
