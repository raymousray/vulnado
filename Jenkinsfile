pipeline {
    agent any

    stages {
        stage('OWASP DependencyCheck') {
            steps {
                script {
                    // Run OWASP DependencyCheck with additional arguments
                    dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
                }
            }
        }
    }

    post {
        always {
            // Add post-build action to analyze DependencyCheck reports using the Warnings Next Generation Plugin
            recordIssues(
                tools: [dependencyCheck()],
                aggregatingResults: true, // Aggregate results if needed
                ignoreFailedBuilds: false, // Ignore failed builds during analysis
                sourceCodeEncoding: 'UTF-8', // Specify source code encoding
                // Add more customization options as needed
            )
        }
    }
}






