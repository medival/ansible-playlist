pipeline {
  agent any

  stages {
    stage('Copy Ansible Playbook from SCM') {
      steps {
        git branch: 'template', changelog: false, credentialsId: 'medival-github', poll: false, url: 'https://github.com/medival/ansible-playlist.git'
      }
    }
    stage('Render file yaml') {
      steps {
        dir('playbooks/roles/base/vars') {
          sh """#!/bin/bash
            sed -i 's/TENANT/${TENANT}/g' main.yml
            sed -i 's/INSTANCE_NAME/${INSTANCE_NAME}/g' main.yml
            sed -i 's/DEPLOY_TO/${DEPLOY_TO}/g' main.yml
            sed -i 's/IMAGE_OS/${IMAGE_OS}/g' main.yml
            sed -i 's/FLAVOR/${FLAVOR}/g' main.yml
            sed -i 's/ADDITIONAL_DISK_NAME/${ADDITIONAL_DISK_NAME}/g' main.yml
            sed -i 's/ADDITIONAL_DISK_SIZE/${ADDITIONAL_DISK_SIZE}/g' main.yml
            sed -i 's/NIC/${NIC}/g' main.yml
            sed -i 's/NETWORK_NAME/${NETWORK_NAME}/g' main.yml
            sed -i 's/NETWORK_IP/${NETWORK_IP}/g' main.yml
            sed -i 's/KEYPAIR/${KEYPAIR}/g' main.yml
            sed -i 's/ROOT_DISK_SIZE/${ROOT_DISK_SIZE}/g' main.yml
          """
        }
      }
    }
    stage('Copy Ansible Playbook to Ansible Machine') {
      steps {
          sh 'ls -lah'
          sh 'pwd'
          sh 'cp -rf ${WORKSPACE}/ ~/test/${BUILD_NUMBER}'
          sh 'ls -lah'
          sh 'cd ~/test/'
          sh 'pwd'
          sh 'cat ~/test/${BUILD_NUMBER}/playbooks/roles/base/vars/main.yml'
      }
    }
    stage('Run Ansible Playbook') {
      steps {
        echo 'RUN Ansible Playbook'
      }
    }
  }
}
