pipeline {
    agent any

    stages {
        stage('Testing Strong Enforcement') {
            steps {
                script {
                    echo "Attempting ArmorCode validation with ArmorCode token"
                    armorcodeReleaseGate(
                            product: 'chirag_g',
                            subProduct: 'cmsf',
                            env: 'Production',
                            maxRetries: 2,
                            mode: 'block'
                    )
                }
            }
        }

        stage('Should Not Run') {
            steps {
                echo "ENFORCEMENT BROKEN: Second stage ran after failure!"
            }
        }
    }

    // Optional: Post-actions block to handle different build outcomes
    post {
        failure {
            echo "ArmorCode validation failed. Stopping pipeline."
        }
        success {
            echo "ArmorCode validation passed successfully."
        }
    }
}