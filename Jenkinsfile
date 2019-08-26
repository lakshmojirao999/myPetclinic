pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
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
    }
}
