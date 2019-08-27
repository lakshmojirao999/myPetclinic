pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
       /* stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy'){
            steps {
                  
                  echo "Deploying to Tomcat "
                  sh 'curl -s --upload-file target/petclinic.war "http://tomcat:tomcat@192.168.0.34:8080/manager/text/deploy?path=/petclinic&update=true&tag=${BUILD_TAG}"'
            }
        }
	stage('Docker Build'){
        agent dockerfile
         steps{
	 sh 'docker build -t zelar/petclinic:${BUILD_NUMBER} .'
         sh 'docker tag zelar/petclinic:${BUILD_NUMBER} zelar/petclinic:latest'
	 }
	}

        stage('Docker Push'){
          agent { docker 'alpine' }
         steps{
	  withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
	    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
	    sh 'docker push zelar/petclinic:latest'}*/
		
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/lakshmojirao999/myPetclinic.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
      stage('Docker Run'){
        steps{
        sh 'docker run -p 8181:8080 zelar/petclinic'
       }
      }
  }
}
