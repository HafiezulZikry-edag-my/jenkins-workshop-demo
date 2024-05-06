pipeline {

    agent {
        kubernetes {
            // Define podTemplate
            inheritFrom 'wprs-be'
            defaultContainer 'node'
            yamlFile 'pod-template.yaml'
        }
    }

    stages {
        stage('First step') {
            steps {
                echo 'Hello world';
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing'
                script {
                    try {
                        sh 'npm test'
                    } catch (err) {
                        echo 'Tests failed'
                        throw err
                    }
                }
            }
        }
    }
}