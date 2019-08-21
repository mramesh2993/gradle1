node{
    stage('SCM CheckOut'){
        git 'https://github.com/mramesh2993/containerDeploy.git'
    }
    stage('Build'){
        def mvnHome = tool name: 'mvn3.3', type: 'maven'
        sh "$mvnHome/bin/mvn package"
    }
    stage('move the artifactory to the ansible control server')
    {
    sh sshPublisher(publishers: [sshPublisherDesc(configName: 'ansiblehost', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//playbook', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '$workspace/target/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
      stage('Playbook runner')
    {
  #  sshPublisher(publishers: [sshPublisherDesc(configName: 'ansiblehost', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '/opt/playbook/copyplayboom.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
}
}
