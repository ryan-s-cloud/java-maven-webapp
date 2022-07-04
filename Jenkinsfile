pipeline {
    agent any
    
    tools
    {
       maven "Maven"
    }
     
    stages {
      stage('checkout') {
            steps {
               git branch: 'master', url: 'https://github.com/ryan-s-cloud/java-maven-webapp.git'
            }
        }
         stage('Tools Init') {
            steps {
               script {
                 echo "PATH = ${PATH}"
                 echo "M2_HOME = ${M2_HOME}"
                 def tfHome = tool name: 'Ansible'
                 env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
               }  
            }
        }

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
