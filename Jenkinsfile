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
            discordSend description: "Jenkins Pipeline Build", footer: "Footer Text", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: "https://discordapp.com/api/webhooks/786937940742897674/lOllyP7lhmaMKZ2z2LdhtN-LcdS5oVm422Fg_ouHaqelKYsv4bxJnUSy6uOrYo9Jav0q"
            httpRequest url: "http://http://192.168.87.129//api/4pyv2rUgbtQINMI1CbGQ2L3zLI4rNMo9W0BaRKC5/lights/4", httpMode: "PUT", requestBody: '{"on":true, "sat":254, "bri":254,"hue":30000}'
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