pipeline {
    agent { dockerfile true }
                  }
    }
    stages {
       agent { docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
    }
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
