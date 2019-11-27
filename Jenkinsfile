pipeline {
  agent {label '!jenkins-master'}
    stages {
      stage('Cleaning after previous builds') {
        steps {
	  sh 'rm -rf landing'
	}
      }
      stage('Cloning GitHub repo') {
        steps {
          sh """
	  git clone https://github.com/kastilochagin/ansible.git landing
	  cd landing 
	  """
        }
      }
      stage("Initiating Ansible roles") {
        steps {
          ansiblePlaybook(playbook: '/home/jenkins/workspace/CD/landing/playbook.yml')
        }         
      }
      stage('Landing directory removal') {
        steps {
	  sh """
	  cd ..
	  rm -rf landing
	  """
	}
      }
    }        
}
