pipeline {
    agent {
        docker { 
            image 'node:7-alpine' 
            label 'support_ubuntu_docker'
             }
    }
    stages {
       agent { dockerfile true }
	 stage('Docker Build'){
         steps{
         sh 'docker image build -t zelar/petclinic:${BUILD_NUMBER} .'
         sh 'docker tag zelar/petclinic:${BUILD_NUMBER} zelar/petclinic:latest'
         }
        }
		 stage('Docker Push'){
         steps{
          withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
            sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
            sh 'docker push zelar/petclinic:latest'}
    }
}
}
}
