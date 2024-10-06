pipeline {
    agent any

    tools {
        maven 'maven3' // Use the name of your Maven installation
        jdk 'jdk11'    // Use the correct name of your JDK installation in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                // Pull code from Git repository
                git branch: 'main', 
                    changelog: false, 
                    credentialsId: '18b9699d-39ff-4a23-90d3-4638e6169ecf', 
                    poll: false, 
                    url: 'https://github.com/mdsyedali8/Git_Importer.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh "mvn clean package"
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh "mvn test"
            }
        }

        stage('Deploy') {
            when {
                // Only deploy when branch is main
                branch 'main'
            }
            steps {
                // Example deploy step
                echo 'Deploying to environment...'
            }
        }
    }

    post {
        always {
            // Clean up after build
            sh 'rm -rf target'
        }
        success {
            // Notify on success
            echo 'Build succeeded'
        }
        failure {
            // Notify on failure
            echo 'Build failed'
        }
    }
}
