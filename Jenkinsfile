pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build the .NET Core application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
            echo '"Get the Driver Path ${ChromeDriverPath}"'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the app in IIS server'
      }
    }

  }
  environment {
    ChromeDriverPath = 'C:\\Driver\\Path\\'
  }
}