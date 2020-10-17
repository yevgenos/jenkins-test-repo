pipeline {

  agent any
  tools {
     ###"accessing build tools for my projects"###
      maven 'SpecificToolName' ---------> "tools are managed in jenkins tools&configurations"######
  }
  environment {
    NEW_VERSION = '1.3.0'
    SERVER_CREDENTIALS = credentials('credentialID') -------> "requesting the credentials from jenkins server"######
  }
  stages {
    stage("build") {
      steps {
        echo 'building the application...'
        echo "building version ${NEW_VERSION}"
        echo 'building ver ${NEW_VERSION}'
      }
    }
    
    stage("test") {
      steps {
        echo 'testing the application...'
      }
    }
    
    stage("deploy") {
      steps {
        echo 'deploying the application...'
        sh "${SERVER_CREDENTIALS}" ---> "using the previously requedsted credentials"
        withCredentials([
            usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)    
        ]) {
          sh "some script ${USER} ${PWD}" ----> "using the credentials directly, requires: Credentials and Credentials Binding"
        }
      }
    }
  }
}
