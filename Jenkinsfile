node {
    git([url: "https://github.com/isaaccupa/ansible.git", branch: "master"])
}
pipeline {
  agent any;
  stages {
    stage('Git') {
      steps {
        echo '> Checking out the Git version control ...'
        checkout scm
      }
    }
    stage("deploy") {
      steps {
        echo "Initiating Deploy."
        ansiColor('xterm') {
          ansiblePlaybook (
            colorized: 'true',
            disableHostKeyChecking: true,
            forks: 100,
            installation: 'Ansible',
            inventory: 'hosts',
            playbook: 'deploy.yml'
          )
        }
      }
    }
  }
}