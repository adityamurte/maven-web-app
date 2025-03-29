@Library('slacksharedlib') _

pipeline{
    agent any

    tools{
        maven 'maven'
    }

    stages{
        stage("checkout"){
            steps{
              slackshared('STARTED')
              git credentialsId: 'a938564c-b099-4d3f-8e7c-0c3aec4b4c2c', url: 'https://github.com/adityamurte/maven-web-app.git'
            }
        }

        stage("build"){
            steps{
                sh "mvn clean package"
            }
        }
    }
    post {
     success {
           println "Current Build Result: ${currentBuild.result}"
           slackshared(currentBuild.result)
      }
      failure {
           println "Current Build Result: ${currentBuild.result}"
            slackshared(currentBuild.result)
      }
}

}
