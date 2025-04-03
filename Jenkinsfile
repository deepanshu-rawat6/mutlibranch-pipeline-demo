pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    armorcodeReleaseGate(product: "120_Days_Review", subProduct: "120_Days_Review", env: "Production", mode: "block")
                }
            }
        }
    }
}
