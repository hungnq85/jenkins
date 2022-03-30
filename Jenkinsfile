pipeline {
    // agent any
	
	
	def remote_dir = 'D:/TMP'
	def config_dir = './APP'
	
	// def secrets = [
    //     [path: 'jenkins/h2h/secrets', engineVersion: 2, secretValues: [
    //         [vaultKey: 'key', envVar: 'key_private']]],
    //     [path: 'jenkins/h2h/credential', engineVersion: 2, secretValues: [
    //         [vaultKey: 'USER', envVar: 'user_ansible'],
    //         [vaultKey: 'PASSWORD', envVar: 'password_ansible']]]
    //     ]
    // def configuration = [vaultUrl: 'https://vault-dso.techcombank.com.vn',
    //                      vaultCredentialId: 'jenkins-approle',
    //                      engineVersion: 2]
	
	
	stage("Checkout SCM"){
        cleanWs()
        checkout scm
    }

    stages {
        stage('Build') {
            steps {
                echo 'Start building..'
				
				echo remote_dir
				
				echo config_dir
				
				sh """
                    export ANSIBLE_FORCE_COLOR=true
                    ansible-playbook -i inventory/hosts --extra-vars "remote_dir=${remote_dir} config_dir=${config_dir}" playbook-deploy.yml
				"""
				echo 'End building!'
				
            }
        }
        stage('Test') {
            steps {
                echo 'Start testing..'
				
				echo 'End testing!'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Start deploying....'
				
				echo 'End deploying!'
            }
        }
    }
}

// node("dr-ito-jenkins-slave-common-01"){
    // def remote_dir = 'E:/H2HRollout-demo'
    // def config_dir = './H2H_RECONCILIATION'
    

    

    // // withVault([configuration: configuration, vaultSecrets: secrets]) {
    // // stage("Get Private Key"){
    // //     //def privateKey = "${key_private}"
    // //     writeFile file: 'keys/TcbTestSecretKey.gpg', text: user_ansible
    // //     sh '''
    // //     cat ./keys/TcbTestSecretKey.gpg
    // //     '''
    // // }
    // stage("Run Ansible-playbook Deploy"){
            // sh """
            // export ANSIBLE_FORCE_COLOR=true
            // ansible-playbook -i inventory/hosts --extra-vars "remote_dir=${remote_dir} config_dir=${config_dir}" playbook-deploy.yml
            // #ansible-playbook -i inventory/hosts --extra-vars "remote_dir=${remote_dir} config_dir=${config_dir}" playbook-service.yml
            // """
    // }
    // // }
    // // stage ('print'){
    // //     sh '''
    // //     cat ./keys/TcbTestSecretKey.gpg
    // //     '''
    // // }
// }
