pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Hazzimov/ansible'
            }
        }
        
        stage('Run Ansible Playbook') {
            steps {
                sh '''
                cd $WORKSPACE
                ls -l
                ansible-playbook -i inventory/inventory.ini playbooks/node_app.yml
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Node.js app deployed successfully!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
