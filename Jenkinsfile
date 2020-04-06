  
pipeline {
  agent any
  
  parameters {
    string(name: 'branch', defaultValue: 'master', description: '디플로이할 대상 브랜치를 입력하세요.')
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
        b="${branch}";
        echo "${b}"
        echo "${b}".replace(\"/\", \"_\")
        
        '''
      }
    }

  }
}
