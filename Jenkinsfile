pipeline{
    agent any
    stages{
        stage("git checkout"){
            when{
            branch "feature"
            }
            steps{
                git branch: 'main', credentialsId: '1234', url: 'https://github.com/ankithbolem/my-jenkins-job-2022'
            }
        }
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
