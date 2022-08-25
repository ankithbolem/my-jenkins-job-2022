pipeline{
    agent any
    triggers {
        cron ("* 10 * * *")
    }
    stages{
        stage("maven build"){
            when{
            branch "develop"
            }
            steps{
                sh 'mvn clean package'
            }
        }
        stage("tomcat deploy"){
            when{
            branch "main"
            }
            steps{
             echo "hey ankith"
            }
        }
    }
}
