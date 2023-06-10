pipeline {

   agent {
     node {
      label 'workstation'
     }
   }
   parameters {
       choice(choice(name: 'dev', choices: ['dev', 'prod'], description: 'Pick environment'))
       string(name: 'component', defaultValue: '', description: 'Pick component')
   }

   stages {
     stage('Ansible') {
       steps {
       sh 'ansible-playbook -i ${component}-${env}-pavan345.online, roboshop.yml -e ansible_user=centos -e ansible_password=DevOps321 -e env=${env} -e role_name=${component}'
       }
     }

   }

   post {
    always {
    cleanws ()
     }
   }


}