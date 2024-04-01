pipeline {
    agent any
    
    tools {
        maven 'maven-3.9.6'
    }

    stages {
        stage('checkout') {
            steps {
                // One or more steps need to be included within the steps block.
                git branch: 'main', url: 'https://github.com/DevopsTraining-Harish/maven-project.git'
            }
        }
        stage('build') {
            steps {
                echo 'Build'
                bat 'mvn compile'
      
            }
        }
        stage('test') {
            steps {
                echo 'test'
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                bat 'mvn test'
            }
        }
        stage('Mail') {
            steps {
                echo 'Sending mail'
                
                emailext body: '''Hi Team,


                $JOB_NAME  - Build $BUILD_NUMBER  - $BUILD_STATUS:

                Check console output at $BUILD_URL to view the results.

                Thanks
                Harish Narla''', recipientProviders: [buildUser(), developers()], subject: 'JENKINS [ $JOB_NAME ] - Build $BUILD_NUMBER - $BUILD_STATUS!', to: 'devopstraining.harish@gmail.com'
            }
        }
    }
}
