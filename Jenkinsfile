pipeline {
  agent any 
  
  stages {
    stage('Build') {
      steps {
        sh 'mvn compile'
      }
    }
    
     
    stage('Test') {
      steps {
        sh 'mvn test'
      }
     post {
      always {
        junit '**/TEST*.xml'

      }
     }
  }
  stage('newman') {
        steps {
           sh ' newman run Spring_PetClinic.postman_collection.json --environment PetClinic_Environment.postman_environment.json --reporters junit '
              }
            post {
                  always {
                          junit '**/TEST*.xml'
                         }
                  }
        }

  }
}
