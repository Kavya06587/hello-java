pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Code checkout done automatically by Jenkins SCM"
            }
        }

        stage('Compile') {
            steps {
                sh '''
                    echo "Creating output folder..."
                    mkdir -p out

                    echo "Compiling Java code..."
                    javac -d out src/Hello.java
                '''
            }
        }

        stage('Run') {
            steps {
                sh '''
                    echo "Running Java program..."
                    java -cp out Hello
                '''
            }
        }
    }

    post {
        always {
            echo "Pipeline completed (success or failure)."
        }
        success {
            echo "✅ Build SUCCESS!"
        }
        failure {
            echo "❌ Build FAILED!"
        }
    }
}
