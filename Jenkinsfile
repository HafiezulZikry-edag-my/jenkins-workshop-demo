pipeline {

    agent {
        kubernetes {
            // Refer to the pod template file
            yaml file: 'pod-template.yaml'
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

        stage('Run tests') {
            try {
                steps {
                    sh 'npm test'
                }
            } catch (err) {
                echo 'Tests failed'
                currentBuild.result = 'FAILURE'
            }
        }
    }
}