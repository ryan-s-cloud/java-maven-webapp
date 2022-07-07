pipeline {
    agent any
    
    environment {
      SSH_KEY = credentials('ANSIBLE_SSH_KEY')
    }
    
    tools {
       maven "Maven"
       git "Default"
    }
     
    stages {
       stage('Execute Maven') {
          steps {
             sh 'mvn package'             
          }
       }
         
       stage('Ansible Deploy') {
          steps {
              sh "ansible-playbook main.yml -i hosts.yml --user ansible --key-file ${SSH_KEY}"
          }
       }
    }
}
