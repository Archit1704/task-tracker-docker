
stage('SonarQube Analysis') {
    steps {
        script {
            def scannerHome = tool 'SonarScanner'

            withSonarQubeEnv('SonarQube') {
                sh """
                    ${scannerHome}/bin/sonar-scanner \
                      -Dsonar.projectKey=devops-demo \
                      -Dsonar.projectName=devops-demo \
                      -Dsonar.sources=. \
                      -Dsonar.exclusions=**/node_modules/**,**/coverage/**,**/dist/**,**/.git/**
                """
            }
        }
    }
}

stage('Quality Gate') {
    steps {
        timeout(time: 5, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
