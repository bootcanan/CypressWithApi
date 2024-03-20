pipeline{

  agent any
  stages{
stage('Clone Git Repo'){
   steps{

       git 'https://github.com/bootcanan/CypressWithApi.git'

   }


}

stage('Install Dependencies'){

    steps{

        bat 'npm install'
    }
}
stage('Run Tests'){

     steps{


        bat 'npx cypress run --reporter mochawesome --reporter-options reportDir="reporter-config.json",overwrite="false",html="false",json="true"'
     }

}
stage('Publish HTML Report'){
   steps{

         publishHTML([ allowMissing:false,alwaysLinkToLastBuild:false,keepAll:false, reportDir:'reporter-config.json',reportFiles: 'report.html',reportName: 'HTML Report', reportTitles: ''])

   }


}
  }


}