pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Hazzimov/ansible'
            }
        }

        stage('Install Ansible') {
            steps {
                sh '''
                if ! command -v ansible >/dev/null 2>&1; then
                    sudo apt update -y
                    sudo apt install -y ansible
                fi
                '''
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
