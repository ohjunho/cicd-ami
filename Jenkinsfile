pipeline {
  agent any
  stages {
    stage('Git clone') {
      steps {
        git(url: 'https://github.com/opsflex/ami.git', branch: 'master', changelog: true)
      }
    }

    stage('Test') {
      steps {
        input(message: 'os?', ok: 'ubuntu')
      }
    }

    stage('Image Build') {
      steps {
        sh '''
cd /var/lib/jenkins/workspace/cicd-ami_master/packer/build_ubuntu
/opt/packer/packer build gitlab-ami.json
        '''
      }
    }

  }
}