pipeline {
    agent any
    triggers{
        pollSCM('* * * * *')
    }
    stages {
        stage('Build') {
            steps {
                // Run Maven on a Unix agent.
                sh './mvnw clean package'
            }
        }
    }

    post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                always {
                    junit '*target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
}
