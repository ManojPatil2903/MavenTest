pipeline {
    agent any

    environment {
        GIT_CREDENTIALS_ID = 'GITHUB-CRED' // Replace with your Jenkins credential ID
        GIT_REPO_URL = 'https://github.com/ManojPatil2903/MavenTest.git' // Replace with your GitHub repository URL
    }

    stages {
        stage('Checkout Repository') {
            steps {
                script {
                    try {
                        withCredentials([usernamePassword(credentialsId: env.GIT_CREDENTIALS_ID, usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
                            bat """
                                git clone https://%GIT_USERNAME%:%GIT_PASSWORD%@github.com/your-username/your-repo.git
                            """
                        }
                        echo "GitHub credentials are valid. Repository cloned successfully."
                    } catch (Exception e) {
                        echo "GitHub credentials test failed: ${e}"
                        error("Failed to authenticate with GitHub.")
                    }
                }
            }
        }
    }
}
