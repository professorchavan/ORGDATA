pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', // Replace 'main' with your branch name
                    url: 'https://github.com/professorchavan/orgdata.git',
                    credentialsId: 'githubcred' // Set up GitHub credentials in Jenkins
            }
        }
        stage('Build') {
            steps {
                echo 'This is a simple pipeline example!'
            }
        }
    }
}
