pipeline {
  agent any
  stages {
    stage('Code checkout') {
      steps {
        git(url: 'git@github.com:krishdumpa/spring-framework-petclinic.git', branch: 'master')
      }
    }

    stage('Build') {
      steps {
        sh '/opt/maven38/bin/mvn clean package '
      }
    }

    stage(' Upload') {
      steps {
        sh 'aws s3 cp target/petclinic.war s3://dev-krishdumpa-artifactory/'
      }
    }

    stage('deploy') {
      steps {
        sh 'scp target/petclinic.war root@10.0.5.204:/opt/tomcat/webapps/'
      }
    }

  }
}