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
    stage('yellow') {
      steps {
        script {
          currentBuild.result = 'UNSTABLE'
	      }
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
              sh "exit 1"
          }
        )
      }
      post {
        failure {
          sh 'echo was failure'
          script {
            currentBuild.result = 'UNSTABLE'
          }
        }
        unstable {
          sh 'echo was unstable'
          script {
            currentBuild.result = 'UNSTABLE'
          }
        }
      }
    }
  }
}
