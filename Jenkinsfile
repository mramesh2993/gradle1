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
        sshPublisher(publishers: [sshPublisherDesc(configName: 'ansiblehost', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//tmp', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
}
