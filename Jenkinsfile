#!/usr/bin/env groovy
node {
  library 'Util'
  message('STARTED', false)

  try {
    stage('SCM checkout') {
      slothCheckout("docker-elk")
      dir('docker-elk') {
        sh 'git branch --set-upstream-to=master master'    
      }
    }

    stage('Docker Build') {
      dir('docker-elk') {
        withEnv(['DOCKER_HOST=unix:///var/run/docker.sock']) {
          sh "docker-compose build"
          sh "docker-compose push"
        }
      }
    }
    
    stage('Starting up elk') {
      dir('docker-elk') {
        sh "docker-compose pull"
        sh "docker-compose up -d"
      }
    }

  } catch (ex) {
    currentBuild.result='FAILURE'
    throw ex
  } finally {
    message(currentBuild.result, false)
  }
  
}


