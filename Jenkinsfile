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
            recordIssues enabledForFailure: true, tool: owaspDependencyCheck(patterns:'**/dependency-check-report.json')
            recordIssues enabledForFailure: true, tools: [java(), javaDoc()]
        }
    }
}






