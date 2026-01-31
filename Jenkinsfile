pipeline {
    agent any

    stages {

        stage('Build') {
            when {
                branch 'main'
            }
            steps {
                echo 'Running full CI pipeline on main branch'
                sh 'mvn clean test'
            }
        }

        stage('Test Only') {
            when {
                branch pattern: "feature/.*", comparator: "REGEXP"
            }
            steps {
                echo 'Running tests for feature branch'
                sh 'mvn test'
            }
        }

        stage('Release Validation') {
            when {
                branch pattern: "release/.*", comparator: "REGEXP"
            }
            steps {
                echo 'Running tests and security scan for release branch'
                sh 'mvn test'
                echo 'Security scan placeholder'
            }
        }
    }
}
