pipeline {
  agent { label "jenkins-node" }

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/cabta/source-maven-java-spring-hello-webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTest=true'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', url: 'http://192.168.56.102:8080')], contextPath: null, war: 'target/hello-world.war'
      }
    }
  }
}

// <<<<<<< HEAD

// =======
// >>>>>>> 9c60e7d87ef5b7b632d37bd34da0007a839f5d38
