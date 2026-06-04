Pipeline {
	agent any

	stages {
	   stage('Show Latest Commit') {
		steps {
		   sh '''
		   git log --oneline -1
		   '''
		}
	}

	stage('Ansible Ping') {
		steps { 
		   sh '''
		   ansible linux -i inventory.ini -m ping
		   '''
		}
	}

	stage('Deploy Website') {
		steps {
		   sh '''
		   ansible-playbook -i inventory.ini deploy-website.yml
		   '''
		}
	}
   }
}
