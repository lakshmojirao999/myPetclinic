
node {
 checkout scm
stage('Kill'){
sh 'var1=$(docker ps -q)'
docker.kill(var1)
}
 def dockerImage
 
  stage('Build image') {
    dockerImage = docker.build("lakshmojirao999/petclinic")

}
 

   stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {

           dockerImage.push('1')
           dockerImage.run('-p 8181:8080')
       }
   }
}
