pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy with Ansible') {
            steps {
                ansiblePlaybook(
                    playbook: 'site.yml',
                    inventory: 'inventory.ini',
                    credentialsId: 'app-servers-ssh-key',
                    colorized: true,
                    disableHostKeyChecking: true,
                    extras: '-v'
                )
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
