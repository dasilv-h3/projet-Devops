pipeline {
  agent any
  stages {
    stage ('Supprimer le workspace') {
      steps {
        deleteDir()
      }
    }
    stage ('Checkout SCM') {
      steps {
        git branch: 'main', credentialsId: '5cef43bd-8341-4f62-a762-4eba7ca47dc5', url: 'https://github.com/dasilv-h3/projet-Devops.git'
      }
    }
    stage ('Build image docker') {
      steps {
        script {
          sh 'docker build -t myimage_nginx .'
          sh 'docker tag myimage_nginx kevinds:myimage_nginx'
        }
      }
    }
  }
}
