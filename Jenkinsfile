node {
    stage('checkout') {
        echo 'Hello chekcing out first ...'
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/NaughtyPhil/maven-jenkins.git']]])
    }
    stage('build') {
        echo 'Beging building...'
        echo env.PATH
        echo env.M2
        def mvnHome = tool 'M3'
        sh 'mvn -Dmaven.test.failure.ignore clean package'
        step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
    }
}
