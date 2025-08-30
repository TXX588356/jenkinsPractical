pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/TXX588356/jenkinsPractical.git'  //download git repo to your local device
            }
        }
        stage('Build') {
            steps { bat 'gradlew build'}  //to build the application using batch file
        }
        stage('Test') {
            steps { bat 'gradlew test'}  //execute batch file gradle test
        }
        stage('Deploy') {
            steps { 
                powershell 'java -jar build/libs/hello-world-java-V1.jar'
            }           
        }    
}

post {  //what to do after pipeline done correctly
        always {
            echo 'Cleaning up workspace' //to not waste space
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
}
