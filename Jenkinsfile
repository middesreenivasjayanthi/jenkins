def branch_nem = scm.branches[0].name
if (branch_nem.contains("*/")) {
    branch_nem = branch_nem.split("\\*/")[1]
    }
echo branch_nem


pipeline {
    agent any
environment {
    brnchname="${branch_nem}"
}
    stages {
        stage ('scm') {
            steps {
                script {
                    
                    echo "br is ${branch_nem}"
                }    
            }
        }
        stage ('validation') {
            steps {
                script {
                    if (brnchname == "main") {
                    echo "branch name contains private"
                    } 
                    else {
                    echo "branch name does not contain private"
                    }
                }    
            }
        }
        stage ('gitbranches') {
            steps {
                script {
                    git ls-remote
                    git ls-remote origin $BRANCH
                    
                }
            }
        }
    } 
} 
