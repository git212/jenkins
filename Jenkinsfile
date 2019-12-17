pipeline{
    agent any
    environment{
	  PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
	}
    stages{
        stage('SCM Checkout'){
            steps {
                git credentialsId: 'git-1', 
                url: 'https://github.com/git212/jenkins',
                branch: 'master'
            }
        }

        stage('Maven Build'){
            steps{
                sh 'mvn clean package'
            }
        }

        stage('Deploy Dev'){
             steps{
                 sshagent(['tomcat-dev']) {
                    // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@18.217.237.212 /tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/6pmwebapp.war  ec2-user@18.217.237.212:/tomcat8/webapps/"
                    // start tomcat
                    sh "ssh ec2-user@18.217.237.212 /tomcat8/bin/startup.sh"
                }
            }
        }
    }
    post{
        success{
           mail bcc: '', body: 'successfully deployed in jenkins', cc: '', from: '', replyTo: '', subject: 'successfully deployed', to: 'mahantabharat312@gmail.com'
        }

    }        
}
