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
            echo "Get the Driver Path ${ChromeDriverPath}"
          }
        }

        stage('Test Log') {
          environment {
            LocalVariable = "HelloLocal"
          }
          steps {
            writeFile(file: 'LogTestFile.txt', text: "This is the ChromeDriverPath ${ChromeDriverPath} and localvariable Value ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        when  {
          branch 'master'
        }
        stage('Deploy') {
          steps {
            input(message: 'Do you want to Deploy', id: 'OK')
            echo 'Deploying the app in IIS server'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts 'LogTestFile.txt'
          }
        }

      }
    }

  }
  environment {
    ChromeDriverPath = 'C:\\Driver\\Path\\'
  }
}