pipeline {
     agent any
     stages {
          stage("Compile") {
               steps {
                    sh "/usr/bin/mvn compile"
               }
          }
          stage("Unit test") {
               steps {
                    sh "/usr/bin/mvn test"
               }
          }
     
    
stage("Package") {
     steps {
          sh "/usr/bin/mvn package"
     }
}
stage("Docker build") {
     steps {
      
          sh "docker build -t practice_tomcat ."
     }
}

stage("Deploy or created tomcat container") {
     steps {
  
          sh "docker run -d -it -v /var/lib/jenkins/workspace/docker-web-example-pipeline/target/:/usr/local/tomcat/webapps/ -p 8091:8080 --name Testtomcat practice_tomcat"
     }
}

     }
  post {
     always {
          sh "echo 'Verify if all OK'"
     }
}
}
