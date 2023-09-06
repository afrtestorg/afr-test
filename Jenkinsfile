script {
    echo "Checkout ${ghprbAuthorRepoGitUrl} branch ${ghprbActualCommit} "
    ci_git_branch="${ghprbActualCommit}"
    ci_git_url = "${ghprbAuthorRepoGitUrl}"
 
}

pipeline {
    agent any
    stages {
        stage('SCM') {
            options {
                timeout(time: 5, unit: 'MINUTES')
            }
            steps {
                // echo "Checkout ${ghprbAuthorRepoGitUrl} branch ${ghprbActualCommit} "
                //ci_git_branch="${ghprbActualCommit}"
                // ci_git_url = "${ghprbAuthorRepoGitUrl}"
                /* Checkout CI Repo */
                // sh cat ./Jenkinsfile

                checkout([$class: 'GitSCM',
                        branches: [[name: ci_git_branch]],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [[$class: 'WipeWorkspace'],
                        [$class: 'CleanCheckout'],
                        [$class: 'CleanBeforeCheckout']],
                        submoduleCfg: [],
                        userRemoteConfigs: [[credentialsId: 'afrtestuserpassword',
                        url: ci_git_url]]])
                        
                }
            }
    
    
        stage('build') {
            steps {
                echo "uypdate 1"
                echo 'mvn --version'
                echo 'IN checked out version'

                //sh cat ./Jenkinsfile
            }
        }
    }
}