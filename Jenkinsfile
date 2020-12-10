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
                echo "Building the solution"
            }
        }
        stage("Test") { 
            steps {
                echo "Testing the solution"
            }
        }
        stage("Deliver") { 
            steps {
                echo "Delivering the solution"
            }
        }
    }
    post {
        always {
            echo "Pipeline has completed"
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
    }
}