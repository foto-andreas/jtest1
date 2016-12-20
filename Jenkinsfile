pipeline {
  agent docker:'frekele/gradle'
  stages {
    stage('test') {
      steps {
        sh 'gradle --version'
	      sh 'java -version'
      }
    }
    stage('build') {
      steps {
        sh 'gradle tasks'
      }
    }
    stage("parallel") {
      steps {
        parallel (
          "Firefox" : {
            sh "echo testing FFX"
            sh "echo more steps"
          },
          "Chrome" : {
            sh "echo testing Chrome"
            sh "echo more steps"
          }
        )
      }
    }
  }
}
