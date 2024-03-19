pipeline {
    agent any

    environment {
        SSH_KEY = credentials('SSH_KEY')
        
    }

    stages {
        stage('Run Ansible Playbook') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'SSH_KEY', keyFileVariable: 'SSH_KEY')]) {
                        sh '''
                            ansible-playbook -i my_ansible_project/inventory/hosts my_ansible_project/install_services_playbook.yml --private-key=$SSH_KEY
                        '''
                    }
                }
            }
        }
    }
}
