pipeline {
    agent any

    environment {
        // Define any environment variables you need
        JAVA_HOME = tool name: 'JDK 11', type: 'jdk'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the GitHub repository
                git url: 'https://github.com/sejal005/CICD-pipeline.git', branch: 'develop'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Example for Java with Maven
                    sh 'mvn clean install'

                    // Example for Node.js
                    // sh 'npm install'
                    // sh 'npm run build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Example for Java with Maven
                    sh 'mvn test'

                    // Example for Node.js
                    // sh 'npm test'
                }
            }
        }
        stage('Run') {
            steps {
                script {
                    // Start the application (example for a Java application)
                    sh 'nohup java -jar target/your-app.jar &'

                    // Example for Node.js
                    // sh 'nohup node server.js &'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy the application (e.g., copy files to a server)
                    sh 'scp -i /path/to/privatekey target/your-artifact user@yourserver:/path/to/deploy/'

                    // You could also trigger a deployment tool, like Ansible or Docker
                    // sh 'ansible-playbook -i inventory deploy.yml'
                }
            }
        }
    }

    post {
        always {
            echo 'This will always run, regardless of the build result.'
        }
        success {
            echo 'This will run only if the build succeeds.'
        }
        failure {
            echo 'This will run only if the build fails.'
        }
    }
}
