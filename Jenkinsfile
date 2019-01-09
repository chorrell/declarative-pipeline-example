#!/usr/bin/env groovy

pipeline {
  agent any
  
  environment {
    VERSION = '1.0.0'
  }
  
  stages {
    stage('Build') {
      steps {
        echo "Building ${VERSION}"
      }
    }
  }
}
