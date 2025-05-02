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
        git branch: 'main', credentialsId: '9f643542-c4b4-4e98-8868-7fca8e5feae2', url: 'https://github.com/dasilv-h3/projet-dev01.git'
      }
    }
    stage ('Build image docker') {
      steps {
        script {
          sh 'docker build -t myapp-image .'
          sh 'docker tag myapp-image kevinds:myapp-image'
        }
      }
    }
    stage ('Deploiement application') {
      steps {
        script{
          sh 'docker rm -f $(docker ps -a -q) | xargs -r docker rm -f'                  
          sh 'docker run -d --name myapp --hostname myapp -p 8088:80 myapp-image'
        }
      }
    }
  }
}
