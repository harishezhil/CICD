pipeline {
    agent any
    environment {
        WORKSPACE = "H:\\nextrurn\\new_jenkins_home\\workspace\\EXERCISE_4"
    }
    stages {
        stage('Changing Directory') {
            steps {
                script {
                    echo "Changing Directory.."
                    dir(env.WORKSPACE) {
                        echo "Directory changed to ${env.WORKSPACE}"
                        echo "Installing Dependencies.."
                        bat 'npm install'
                        echo "Running Tests.."
                        bat 'npm test'
                        echo "Building the project.."
                        bat 'npm run build'
                        echo "Deploying the application by copying the build folder to a deployment directory..."
                        bat "xcopy ${env.WORKSPACE}\\\\dist ${env.WORKSPACE}\\\\deployment-directory /E /I /H /Y"
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'This will always run after the pipeline finishes.'
        }
        success {
            echo 'This will run if the pipeline succeeds.'
        }
        failure {
            echo 'This will run if the pipeline fails.'
        }
    }
}
