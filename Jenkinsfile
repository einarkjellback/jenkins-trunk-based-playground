pipeline {
    agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
    stages {
        stage('build') {
            steps {
                checkout (
                    poll: true,
                    changelog: false, 
                    scm: [
                        $class: 'GitSCM', 
                        // branches: [[name: ":release-\\d+\\.\\d+\\.\\d+"]], 
                        branches: [[name: ":release"]],
                        extensions: [], 
                        userRemoteConfigs: [[url: 'git@github.com:einarkjellback/jenkins-trunk-based-playground.git']]
                    ]
                )
                sh 'mvn --version'
            }
        }
    }
}