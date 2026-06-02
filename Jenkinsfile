pipeline {
	agent any

	stages {
	   stage('Show Latest Commit') {
		steps {
		   sh '''
		   cd /var/lib/jenkins/ansible-lab
		   git log --oneline -1
		   '''
		}
	}

	stage('Ansible Ping') {
		steps { 
		   sh '''
		   cd /var/lib/jenkins/ansible-lab
		   ansible linux -i inventory.ini -m ping
		   '''
		}
	}

	stage('Deploy MOTD') {
		steps {
		   sh '''
		   cd /var/lib/jenkins/ansible-lab
		   ansible-playbook -i inventory.ini deploy-website.yml
		   '''
		}
	}
   }
}
