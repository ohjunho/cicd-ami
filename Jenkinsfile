pipeline {
  agent any
  parameters {
    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
  stages {
    stage('Git clone') {
      steps {
        git(url: 'https://github.com/opsflex/ami.git', branch: 'master', changelog: true)
      }
    }

    stage('Test') {
      steps {
        echo "CHOICE: ${params.CHOICE}"
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
