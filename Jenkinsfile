pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/dong597/jenkinstest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        docker build -t 211.183.3.150/test2/jenkinsweb:1.0 .
        docker push 211.183.3.150/test2/jenkinsweb:1.0
        pwd
        '''
      }
    }
    stage('deploy and service') {
      steps {
        sh '''
        ansible-playbook /var/lib/jenkins/master_ansible.yml
        '''
      }
    }
  }
}