// Example Jenkins Pipeline using runPowerShell shared library
library identifier: 'Common-Library@main', retriever: legacySCM([$class: 'GitSCM', 
    branches: [[name: '*/main']], 
    userRemoteConfigs: [[url: 'https://github.com/singhmanupratap/Common-Library.git', 
                        credentialsId: scm.userRemoteConfigs[0].credentialsId]]])

pipeline {
    agent { label 'Windows' }
    
    stages {
        stage('Multiple Parameter Examples') {
            steps {
                script {
                    echo "=== Multiple Custom Parameters ==="
                    runPowerShellonRemote([
                        Date: "2025-11-09",
                        UserName: "jenkins",
                        RemoteHost: "192.168.1.120",
                        RemoteUser: 'TestRemoteUser',
                        RemotePassword: 'TestPass123!',  // Don't do this in production!,
                        RemoteFile: "D:\\Users\\singh\\source\\repos\\JenkinsSetUp\\scripts\\sample.ps1"
                    ])
                }
            }
        }
    }
    
    post {
        success {
            echo "PowerShell execution completed successfully!"
        }
        failure {
            echo "PowerShell execution failed. Check the logs for details."
        }
        always {
            echo "Pipeline execution finished."
        }
    }
}