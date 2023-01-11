


pipeline {
    agent any

    stages {
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
