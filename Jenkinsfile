pipeline {
  agent any
  
  parameters {
    string(name: 'branch', defaultValue: 'feature/CMSA-407', description: '디플로이할 대상 브랜치를 입력하세요.')
    choice(name: 'OS_Type', choices: ['awslinux2', 'ubuntu'], description: 'OS를 선택하세요.')
    choice(name: 'Target_Image', choices: ['gitlab', 'jenkins', 'sonarqube'], description: 'AMI를 만들 대상을 선택하세요.')
  }
  
  stages {
    stage('Git clone') {
      steps {
        git(url: 'https://github.com/opsflex/ami.git', branch: "${branch}", changelog: true)
      }
    }

    stage('Image Build') {
      steps {
        sh '''
          b=`echo "${branch}" | awk -F " " '{ gsub("/", "_"); print $1}'`
          echo "${b}"
          /opt/packer/packer build "/var/lib/jenkins/workspace/cicd-ami_${b}/packer/build_${OS_Type}/${Target_Image}-ami.json"
        '''
      }
    }

  }
}
