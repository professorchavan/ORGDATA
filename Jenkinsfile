pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/your-username/your-repository.git' // Replace with your repository URL
        GIT_BRANCH = 'main' // Replace with your branch name
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    echo "Checking out the code from ${env.GIT_REPO} on branch ${env.GIT_BRANCH}"
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: env.GIT_BRANCH]],
                        userRemoteConfigs: [[url: env.GIT_REPO]]
                    ])
                }
            }
        }

        stage('Track Changes') {
            steps {
                script {
                    echo 'Checking for changes...'
                    
                    def lastCommitHash = sh(
                        script: 'git rev-parse HEAD',
                        returnStdout: true
                    ).trim()

                    def changes = sh(
                        script: "git diff-tree --no-commit-id --name-only -r ${lastCommitHash}",
                        returnStdout: true
                    ).trim()

                    if (changes) {
                        echo "Files changed in the last commit:"
                        echo "${changes}"
                    } else {
                        echo "No changes detected in the last commit."
                    }
                }
            }
        }

        stage('Notify or Perform Actions') {
            steps {
                script {
                    // Example action: Logging or notifying a team
                    echo "This is where you can perform actions based on detected changes."
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed."
        }
    }
}
