pipeline {
    agent {
        label 'docker'
    }

    stages {

        stage('build from a docker file') {
            steps {
                script {
                    sh 'docker build -t ahmedgamil/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('run those tests') {
            steps {
                script {
                    // Make sure tests run once and exit (no watch mode)
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true ahmedgamil/docker-react npm test -- --watchAll=false'
                }
            }
        }

    }
}
