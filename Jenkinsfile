pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/pmohd6065-ux/Trading-UI.git'
            }
        }

        stage('Install npm prerequisites') {
            steps {
                // Allow npm audit fix to fail without failing the pipeline
                sh 'npm audit fix || true'

                sh 'npm install'
                sh 'npm run build'

                // Correct way to run commands in a directory
                dir('build') {
                    sh 'pm2 --name Trading-UI start npm -- start'
                }
            }
        }
    }
}
