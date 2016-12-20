pipeline {
  agent docker:'frekele/gradle'
  stages {
    stage('test') {
      steps {
        sh 'gradle --version'
	sh 'java -version'
      }
    stage('build') {
      steps {
        sh 'gradle tasks'
      }
    }
  }
}

