pipeline {

  agent {
    node {
      label 'workstation'
    }
  }

  parameters {
    choice(name: 'env', choices: ['dev', 'prod'], description: 'Pick environment')
    string(name: 'component', defaultValue: '', description: 'component name')

  }

  stages {
      stage('Update Parameter Store') {
        steps {
          sh 'aws ssm put-parameter --name "${env}.${component}.app_version" --type "String" --value "${app_version}" --overwrite'
        }
      }

    stage('Ansible') {
      steps
        sh 'ansible-playbook -i /tmp/inv roboshop.yml -e ansible_user=centos -e ansible_password=DevOps321 -e env=${env} -e role_name=${component}'
      }
    }

  }

  post {
    always {
      cleanWs()
    }
  }

}

