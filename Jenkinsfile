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
                sshagent(['12334']) {
               // copy war file
               sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@10.0.1.163:/opt/tomcat9/webapps"
               // server stop
               sh "ssh -o StrictHostKeyChecking=no ec2-user@10.0.1.163 /opt/tomcat9/bin/shutdown.sh"
               // server start
               sh "ssh -o StrictHostKeyChecking=no ec2-user@10.0.1.163 /opt/tomcat9/bin/startup.sh"
}
            }
        }
    }
}
