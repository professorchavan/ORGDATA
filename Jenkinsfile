pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', // Replace 'main' with your branch name
                    url: 'https://github.com/your-username/your-repository.git',
                    credentialsId: 'github-credentials-id' // Set up GitHub credentials in Jenkins
            }
        }
        stage('Build') {
            steps {
                echo 'This is a simple pipeline example!'
            }
        }
    }
}
