node{
    stage('SCM CheckOut'){
        git 'https://github.com/mramesh2993/mastertwo.git'
    }
    stage('Build'){
        def mvnHome = tool name: 'mvn3.3', type: 'maven'
        sh "$mvnHome/bin/mvn package"
    }
}
