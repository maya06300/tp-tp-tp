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
                    colorized: true,
                    become: true,
                    playbook: 'C:\Users\utilisateur\Desktop\simple-react-app-with-unit-testing-master1/playbook.yml'
                )  
            }
        }
	}
}
