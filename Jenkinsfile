pipeline {
    agent any
    parameters {
            string defaultValue: 'master', description: 'choose this branch to build and deploy', name: ' branchName', trim: false
        
    }
    stages {
        stage ('SCM checkout'){
            steps {
                git branch: "${params['branchName']}",
                url: 'https://github.com/git212/jenkins/6pmwebapp'
            }
        }
    }


}
