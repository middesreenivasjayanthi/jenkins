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

                    git ls-remote jenkins



                    BRANCH='pr_mandate'
                    git ls-remote --exit-code --heads origin $BRANCH 
                    EXIT_CODE=$?

                    if [[ $EXIT_CODE == '0' ]]; then
                        echo "Git branch '$BRANCH' exists in the remote repository"
                    elif [[ $EXIT_CODE == '2' ]]; then
                        echo "Git branch '$BRANCH' does not exist in the remote repository"
                    fi
                    git ls-remote
                    git ls-remote origin $BRANCH
                    
                }
            }
        }
    } 
} 
