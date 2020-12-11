pipeline {
    agent any 
    triggers { // https://www.jenkins.io/doc/book/pipeline/syntax/#triggers
        cron("0 1 * * *") // https://en.wikipedia.org/wiki/Cron + https://crontab.guru/
        pollSCM("* * * * *") // https://en.wikipedia.org/wiki/Cron + https://crontab.guru/ 
    }
    stages {
        stage("Build") { 
            steps {
                sh "dotnet build HelloJenkins.sln"
            }
        }
        stage("Test") { 
            steps {
                unstable "Test stage not implemented"
                echo "Testing the solution"
            }
        }
        stage("Deliver") { 
            steps {
                unstable "Deliver stage not implemented"
                echo "Delivering the solution"
            }
        }
    }
    post {
        always {
            echo "Pipeline has completed"
            emailext to: 'tbmh@easv.dk',
                subject: "Pipeline completed: ${currentBuild.fullDisplayName}",
                body: "${env.BUILD_URL} has completed"
        }
        success {
            echo "Pipeline succeeded"
        }
        aborted {
            echo "Pipeline aborted by user"
        }
        failure {
            echo "Pipeline failed"
        }
        unstable {
            echo "Pipeline has completed with warnings"
        }
    }
}