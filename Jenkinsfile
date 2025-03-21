pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/hasan914/declarative_pipeline'
                }
            }
        }

        stage('Start Multi-Container') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }

        stage('Check Versions') {
            steps {
                script {
                    def nodeVersion = sh(script: "docker exec node_container node -v", returnStdout: true).trim()
                    def mavenVersion = sh(script: "docker exec maven_container mvn -version | head -n 1", returnStdout: true).trim()

                    echo "Node.js Version: ${nodeVersion} Hasan"
                    echo "Maven Version: ${mavenVersion} Hasan"
                }
            }
        }
    }
}
