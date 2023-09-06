pipeline {
    agent any
    stages {
          stage('SCM') {
      options {
        timeout(time: 5, unit: 'MINUTES')
      }
      steps {
        echo "Checkout ${ghprbAuthorRepoGitUrl} branch ${ghprbActualCommit} "
        //ci_git_branch="${ghprbActualCommit}"
        // ci_git_url = "${ghprbAuthorRepoGitUrl}"
        /* Checkout CI Repo */
        sh cat ./Jenkinsfile

        checkout([$class: 'GitSCM',
                 branches: [[name: ${ghprbActualCommit}]],
                 doGenerateSubmoduleConfigurations: false,
                 extensions: [[$class: 'WipeWorkspace'],
                 [$class: 'CleanCheckout'],
                 [$class: 'CleanBeforeCheckout']],
                 submoduleCfg: [],
                 userRemoteConfigs: [[credentialsId: 'afrtestuserpassword',
                 url: ${ghprbAuthorRepoGitUrl}]]])
       
      }
    }
        stage('build') {
            steps {
                echo "uypdate 1"
                echo 'mvn --version'
                sh cat ./Jenkinsfile
            }
        }
    }
}