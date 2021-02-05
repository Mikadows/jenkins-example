pipeline {

    agent any

    stages {

        stage ('Git clone') {
            steps {
                git(
                    url: "https://github.com/Mikadows/jenkins-example.git",
                    branch: "feature-test-pipeline-cucumber"
                )
            }
        }

        stage ('Maven Test') {
            steps {
                sh "mvn test"
            }
        }

        stage ('Maven build') {
            steps {
                sh "mvn package"
            }
        }

        stage('Generate cucumber report') {
            steps {
                cucumber buildStatus: "UNSTABLE",
                         fileIncludePattern: '**/cucumber.json',
                         jsonReportDirectory: 'target'
            }
        }
    }
}
