pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo "Build Docker image"
                bat "docker build -t mypythonflaskapp ."
            }
        }

        stage('Run') {
            steps {
                echo "Run application in Docker Container"

                bat "docker rm -f mycontainer >nul 2>&1 || echo Container does not exist"

                bat "docker run -d -p 5001:5001 --name mycontainer mypythonflaskapp"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}