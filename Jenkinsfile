node{
    stage('SCM CheckOut'){
        git 'https://github.com/mramesh2993/containerDeploy.git'
    }
    stage('Build'){
        def mvnHome = tool name: 'mvn3.3', type: 'maven'
        sh "$mvnHome/bin/mvn package"
    }
    stage("move to s3 artifactory')
          {
              s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'jackpandi', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'ap-south-1', showDirectlyInBrowser: false, sourceFile: '**/**', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 's3-artifact', userMetadata: []
          }
    stage('move the artifactory to the ansible control server')
    {
        sshPublisher(publishers: [sshPublisherDesc(configName: 'ansiblehost', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//tmp//playbook', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
    stage('Deploy to Server')
    {
      
        sshPublisher(publishers: [sshPublisherDesc(configName: 'ansiblehost', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /opt/playbook/copyplay.yml --user ansadm', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
}
