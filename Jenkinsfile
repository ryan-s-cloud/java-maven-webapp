pipeline {
    agent any
    
    tools
    {
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
             sh "ansible-playbook main.yml -i hosts.yml --user jenkins --key-file ~/.ssh/id_rsa"
          }
       }
    }
}
