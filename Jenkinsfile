pipeline {
  agent any

  parameters {
    choiceParam('BRANCH_NAME',${list},'Pick something')
  }

  stages {

    stage('Dynamically generate branches') {
      steps {
        dir('app') {
          git url: "https://github.com/chandralek/learning.git", credentialsId: "GitUserPass"
          sh '''
          git branch -r  | awk -F '/' '{print $2}' |sed -n '2,$ p' > branch.txt
          '''
        }
      }
    }
    stage('Parameterl'){
      steps{
        script{
          list = readFile "${env.WORKSPACE}/app/branch.txt"

        }
      }
    }
  }
}