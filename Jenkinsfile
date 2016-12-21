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
            try {
              sh "echo testing Chrome"
              sh "exit 1"
            } catch (e) {
              currentBuild.result = 'UNSTABLE'
            }
          }
        )
      }
    }
  }
}
