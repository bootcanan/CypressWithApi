pipeline{

  agent any
  stages{


     stage('check out scm') {
            when {
                branch 'main'
            }
            steps {
                checkout scm
            }}
stage('Clone Git Repo'){
   steps{

       sh 'git clone https://github.com/bootcanan/CypressWithApi.git'

   }


}

stage('Install Dependencies'){

    steps{

        sh 'npm install'
    }
}
stage('Run Tests'){

     steps{


        sh 'npx cypress run --reporter mochawesome --reporter-options reportDir="reporter-config.json",overwrite="false",html="false",json="true"'
     }

}}
post{
   
   success{
       publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'reporter-config.json', reportFiles: 'mochawesome.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
   }
   


}
  }


