pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                bat '''
                    if exist out rmdir /s /q out
                    mkdir out
                    javac -d out src\\Hello.java
                '''
            }
        }

        stage('Run') {
            steps {
                bat '''
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
