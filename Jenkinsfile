properties([
    parameters([
        string(defaultValue:'firstvalue', name:'FirstName'),
        string(name:'age')
        ])
    ])
node{
    stage('SCM CheckOut'){
        git 'https://github.com/mramesh2993/mastertwo.git'
    }
    stage('Build'){
        def mvnHome = tool name: 'mvn3.3', type: 'maven'
        sh "$mvnHome/bin/mvn package"
    }
    stage('move to artifactory')
    {
        sh "cp -r /var/lib/jenkins/workspace/one/target/*.war  /tmp/sample/"
    }
      stage('Playbook runner')
    {
    sh "ansible-playbook playme.yml"
}
}
