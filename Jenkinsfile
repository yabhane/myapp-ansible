pipeline{
    agent any   
    environment {
        ENV_HOST_DIR = '/home/sogeti/playbooks/hosts'
        ENV_PLAYBOOK_PATH = '/home/sogeti/playbooks/nginx-install.yml'
    }
    stages{
        stage("Git Checkout"){
            steps{
               git 'https://github.com/yabhane/myapp-ansible.git'
            }
        }
        stage('Ansible Init') {
            steps {
                script {
               def tfHome = tool name: 'ansible2'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
        }
        stage("Ansible Execute"){
            steps {
                sh 'whoami'    
                sh 'ansible-playbook -i ${ENV_HOST_DIR} ${ENV_PLAYBOOK_PATH} --check'
                //ansiblePlaybook credentialsId: 'PrivateKey', disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'apache.yml' 
                //ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'apache.yml'
                //ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'apache.yml'
            }
            
        }
 
    }
}
