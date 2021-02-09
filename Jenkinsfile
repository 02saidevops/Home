pipeline{
    agent any
    tools{
        maven 'Maven'
    }
    stages{
        stage("Git"){
            steps{
                git 'https://github.com/02saidevops/Home.git'
            }
        }
        stage("Build"){
            steps{
                sh "mvn clean install package"
            }
        }
        stage("Deploy"){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''cd /etc/ansible;
ansible-playbook dep.yml''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//etc//ansible', remoteDirectorySDF: false, removePrefix: '/webapp/target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}
