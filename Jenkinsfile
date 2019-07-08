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
        sh "cp -r /var/lib/jenkins/workspace/firstpipe/target/*.war  /tmp/sample/"
    }
    stage('Deploy')
    {
        sh "cp -r /tmp/sample/*.war /opt/apache-tomcat-8.5.42/webapps/"
    }
    stage('Create a file with given build variable values')
    {
        def age1="{params.age}"
        def name1="{params.name}"
        if ( age == '22' ) {
            sh '''#!/bin/bash
            touch $name1
            '''
        }
}
}
