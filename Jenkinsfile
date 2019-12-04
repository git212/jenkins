node{
  stage('SCM Checkout'){
    git 'https://github.com/git212/jenkins'
  }
  stage('Compile-Package'){
    sh 'mvn package'
  }
}
