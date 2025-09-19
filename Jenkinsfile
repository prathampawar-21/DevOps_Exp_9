pipeline {
    // 1. Specify the agent (where to run the pipeline)
    agent any

    // 2. Define the Maven tool to use from Jenkins Global Tool Configuration
    tools {
        maven 'Maven3' // This must match the name you gave in the Jenkins configuration
    }

    // 3. Define the stages of the pipeline
    stages {
       stage('Checkout') {
    steps {
        echo 'Checking out the code...'
        // Explicitly specify the branch 'main'
        git branch: 'main', url: 'https://github.com/prathampawar-21/DevOps_Exp_9.git'
    }
}

        stage('Build') {
            steps {
                // Compiles the Java source code
                echo 'Building the application...'
                bat 'mvn compile' // Use 'sh' on Linux/macOS
            }
        }

        stage('Test') {
            steps {
                // Runs the JUnit tests
                echo 'Running tests...'
                bat 'mvn test' // Use 'sh' on Linux/macOS
            }
        }

        stage('Package') {
            steps {
                // Packages the compiled code into a JAR file
                echo 'Packaging the application...'
                bat 'mvn package' // Use 'sh' on Linux/macOS
            }
        }
    }

    // 4. (Optional) Define actions to run after the pipeline completes
    post {
        success {
            echo 'Pipeline finished successfully! Archiving artifacts...'
            // Save the generated JAR file as a build artifact
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}