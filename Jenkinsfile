pipeline {
	agent {
		docker {
			image 'node:6-alpine'
		}
	}
	environment {
		CI = 'true'
	}
	stages {
		stage('Build') {
			steps {
				sh 'npm install'
			}
		}
		stage('Test') {
			steps { 
				sh 'npm test'
			}
		}
        stage('Deploiement Ansible') {
            steps {
                ansiblePlaybook (
                    inventory: '${WORKPLACE}/inventory.ini',
                    colorized: true,
                    become: true,
                    playbook: '${/var/jenkins_home/workspace}/playbook.yml',
                )  
            }
        }
	}
}
