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
            httpRequest url: "https://api.meethue.com/bridge/x-kzNkJtqMcouSipwETUjiXkJP9BA7N-REZOp5yi/lights/1/state", httpMode: "PUT", requestBody: '{"on": true, "xy": [ 0.7, 0.25 ], "bri": 192, "transitiontime": 10 }', contentType: "APPLICATION_JSON", customHeaders:[[name: "Authorization", value: "Bearer HAP4qGpN8y1alDhringgPRN0B9F0"]]
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