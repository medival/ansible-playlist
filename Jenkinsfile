pipeline {
  agent any
     
  stages {
  	// stage('checkout') {
    //   steps {
    //     git branch: 'task-apt-install', changelog: false, credentialsId: 'medival-github', poll: false, url: 'https://github.com/medival/ansible-playlist/'
    //   }
    // }
    
    stage('Ansible execute'){
        steps {
            ansiblePlaybook credentialsId: 'medival-ssh', installation: 'ansible', inventory: './inventory', playbook: './playbooks/main.yml'
        }   
    }
    
    // stage('Ansible remove package'){
    //     steps{
    //         ansiblePlaybook credentialsId: 'medival-ssh',branch: 'task-apt-remove', installation: 'ansible', inventory: './inventory', playbook: '.playbooks/main.yml'
    //     }
    // }
    
    // 	stage('Ansible check host') {      
    //     steps {        
    //     	dir('.') {
    //          ansiblePlaybook credentialsId: 'medival-ssh', installation: 'ansible', inventory: './ansible_hosts', playbook: './playbooks/ping.yml'
    //          }
    // 	}
    // }
	}
}	
