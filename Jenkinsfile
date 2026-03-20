pipeline {
    agent any

    tools {
        // These names MUST match the names you gave in "Manage Jenkins" -> "Tools"
        maven 'Maven3.9'  
        jdk 'JDK-17'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Fetching code from GitHub...'
                // Specifying the 'master' branch as your code is there
                git branch: 'master', url: 'https://github.com/naveen-nani66/Practice-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling the source code using Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Unit Tests...'
                // This runs your JUnit tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application into a JAR file...'
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Storing the build output (JAR) in Jenkins...'
                // This saves the .jar file so you can download it later from Jenkins UI
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Great job! The Build was Successful 🎉'
        }
        failure {
            echo 'Oops! The Build Failed ❌. Check the Console Output for errors.'
        }
    }
}
