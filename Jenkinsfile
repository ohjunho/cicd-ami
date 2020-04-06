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
        sh '''
choice = input message: 'Choose your option', parameters: [string(defaultValue: 'Option 1', description: 'What am I choosing', name: 'Comment')]
echo $choice
'''
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
