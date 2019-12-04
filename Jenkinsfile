node{
  stage('SCM Checkout'){
    git 'https://github.com/git212/jenkins'
  }
  stage('Compile-package'){
    sh 'mvn package'
  }
}
