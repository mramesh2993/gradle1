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
    stage('Deploy')
    {
        sh "cp -r /tmp/sample/*.war /home/rameshmari156/tomcat9/apache-tomcat-9.0.0.M10/webapps"
    }
    stage('Create a file with given build variable values')
    {
     sh "ansiblePlaybook becomeUser: 'ansadm', installation: 'ansible2', inventory: '/etc/ansible/host', playbook: '/tmp/playme.yml', sudoUser: 'ansadm'"
}
}
