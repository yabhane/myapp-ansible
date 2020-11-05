pipeline{
    agent any   
    
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
                sh 'cat /home/sogeti/playbooks/hosts'
                sh 'ansible-playbook -i hosts /home/sogeti/playbooks/nginx-install.yml --check'
                //ansiblePlaybook credentialsId: 'PrivateKey', disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'apache.yml' 
                //ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'apache.yml'
                //ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'apache.yml'
            }
            
        }
 
    }
}
